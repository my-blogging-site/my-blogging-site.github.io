
Energy performances of houses in the UK are stored in Energy Performance Certificate(EPC). EPC's originate from the European Union’s Energy Performance of Buildings Directive (EPBD) introduced in 2003 to improve building efficiency and reduce energy use. EU Member States at the time had to comply with the Directive within three years of the inception date in 2006.
UK implemented this in 2007, which became a requirement for domestic and non-domestic houses and became mandatory for all homes being sold or rented by 2008. They started with Home Information Packs (HIPs) for domestic properties with four or more bedrooms. HIPs was no longer required in 2010 and the requirement for EPCs continued. EPCs are valid for 10 years. EPC have a scale from A (most efficient) to G (least efficient).

The EPC data itself is shared publically [here](https://epc.opendatacommunities.org). The EPC open communities website let's you bulk download some of the EPC data. **I wanted a way to analyse the data in the EPC data in a certain area and automatically create a report of the data.** In this example, I've picked a sample from Westminster as a sample.

The report includes:
- The total number of EPCs carried out in the local authority
- A graph of the number of EPCs against property type (house, flat, massionette, Bunaglow, Park home)
- A graph of the number of EPCs at energy ratings against number of records

The code is below with some plots that is included in the report:


```python
import pandas as pd
import os
import seaborn as sns
import matplotlib.pyplot as plt
from reportlab.lib.pagesizes import letter
from reportlab.platypus import SimpleDocTemplate, Image, Paragraph, Spacer
from reportlab.lib.styles import getSampleStyleSheet

class OpenBEM:
    def __init__(self, file_path):
        self.file_path = file_path

    def read_data(self):
        """Read data from a csv file"""
        self.df = pd.read_csv(self.file_path, low_memory=False)

    def process_data(self):
        """Process data"""
        energy_rating_order = ['A', 'B', 'C', 'D', 'E', 'F', 'G']
        self.df['CURRENT_ENERGY_RATING'] = pd.Categorical(self.df['CURRENT_ENERGY_RATING'], \
                                                          categories=energy_rating_order, ordered=True)

    def numberEPCs(self):
        """Print results and stats"""
        log_by_la = self.df['LOCAL_AUTHORITY'].value_counts()
        la = self.df['LOCAL_AUTHORITY_LABEL'].value_counts()
        la_name = la.idxmax()
        sum_la_count = log_by_la.sum()

        no_EPCs = f'In the latest data release, there are {sum_la_count} EPC lodgments in \
                    {la_name}'

        return no_EPCs, la_name

    def save_plot(self, figure, plot_name):
        """Save plot to folder"""
        figure.savefig(os.path.join(plot_name))
        plt.close()

    def plot_energy_bands(self, authority_name):
        """Generate and save plot"""
        energy_rating_order = self.df['CURRENT_ENERGY_RATING'].cat.categories
        energy_rating_counts = self.df['CURRENT_ENERGY_RATING'].value_counts().reset_index()
        energy_rating_counts.columns = ['CURRENT_ENERGY_RATING', 'Number of Records']

        plt.figure(figsize= (10, 6))

        sns.barplot(x = 'Number of Records', y = 'CURRENT_ENERGY_RATING', data=energy_rating_counts, \
                    order=energy_rating_order)
        
        sns.barplot(x='Number of Records', y= 'CURRENT_ENERGY_RATING', data=energy_rating_counts,
                    order= energy_rating_order) 

        plt.xlabel('Number of Records')
        plt.ylabel('Current Energy Ratings')
        plt.title('Distribution of Energy Ratings in '+ str(authority_name))
        plt.tight_layout()
        plt.show()
        self.save_plot(plt, 'plots/horizontal_bar_plot_rating_records in ' +str(authority_name)+'.png')

    def plot_property_type_count(self, authority_name):
        plt.figure(figsize=(12,6))
        sns.countplot(x='PROPERTY_TYPE', data=self.df)
        plt.xticks(rotation=45)
        plt.xlabel('Property Type')
        plt.ylabel('Count')
        plt.savefig(os.path.join('plots/bar_chart_count_prop_by_type in '+str(authority_name)+'.png'))
        plt.show()
        plt.close()

    def make_report(self, authority_name, no_EPCs):
        """Making PDF report"""
        pdf_doc = SimpleDocTemplate("reports/open_epc_report_for_"+str(authority_name)+".pdf", pagesize=letter)
        content = []

        # Add title and sub title to report
        title = "Open EPC report for "+str(authority_name)
        content.append(Paragraph(title, getSampleStyleSheet()['Title']))
        content.append(Spacer(1, 12))
        content.append(Paragraph(numberEPC, getSampleStyleSheet()['BodyText']))

        # Add plots to report
        content.append(Image('plots/bar_chart_count_prop_by_type in ' +str(authority_name)+'.png', width =400, height=300))
        content.append(Image('plots/horizontal_bar_plot_rating_records in '+str(authority_name)+'.png', width= 400, height=300))

        # Make report
        pdf_doc.build(content)

# improve design
sns.set(style="whitegrid")
sns.set_palette("viridis")


file_path = 'data/epc-certificates/certificates.csv'
open_epc = OpenBEM(file_path)
open_epc.read_data()
open_epc.process_data()
numberEPC, local_authority_name = open_epc.numberEPCs()
open_epc.plot_energy_bands(local_authority_name)
open_epc.plot_property_type_count(local_authority_name)
open_epc.make_report(local_authority_name, numberEPC)

```


    
![png](/assets/open_bem_report_1_0.png)
    



    
![png](/assets/open_bem_report_1_1.png)
    

