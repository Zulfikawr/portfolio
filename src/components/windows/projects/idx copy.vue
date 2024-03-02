<template>
    <div>
  
        <div class="inner-content">
          <h3 class="heading"><b>ID/X Partners: Final Project</b></h3>
          <h4 class="subtitle">
              Data analysis final project by Rakamin Academy x ID/X Partners.
          </h4>
          
          <div class="badge-grid">
            <img
              class="badge"
              alt="Data Analysis"
              src="https://img.shields.io/badge/-Data Analysis-blue"
            />
  
            <img
            class="badge"
            alt="Python"
            src="https://img.shields.io/badge/-Python-darkblue"
            />

            <img
            class="badge"
            alt="Data Visualization"
            src="https://img.shields.io/badge/-Data Visualization-red"
            />
          </div>
        </div>
  
        <hr> <br>

        <div class="table-of-contents">
          <h3 class="heading">Table of Contents</h3>
          <ul>
            <li><a href="#overview" @click.prevent="scrollToSection('overview')">Project Overview</a></li>
            <li><a href="#prep" @click.prevent="scrollToSection('prep')">Data Preparation</a></li>
            <li><a href="#initial" @click.prevent="scrollToSection('initial')">Initial Data Finding</a></li>
            <li><a href="#feature" @click.prevent="scrollToSection('feature')">Feature Engineering</a></li>
            <li><a href="#in-depth" @click.prevent="scrollToSection('in-depth')">In-Depth Analysis and Visualizations</a></li>
            <li><a href="#suggestions" @click.prevent="scrollToSection('suggestions')">Recommendations</a></li>
          </ul>
        </div>
  
        <div id="overview" class="inner-content">
          <h3 style="text-align: left;">Project Overview</h3>
          <p class="paragraph">
              After spending one month interning virtually at Rakamin Academy x ID/X Partners in a data 
              scientist role, I'm excited to present my final project. This project dives into a detailed 
              analysis of loan data, specifically from ID/X Partners. The dataset covers different aspects 
              of loans, such as loan amounts, interest rates, borrower details, and loan statuses. The aim 
              is to uncover insights into the factors affecting loan performance, visualize trends over 
              time, and provide informed suggestions to enhance business strategies.
          </p>
          <p><b>Tools</b>: <br>
              Jupyter Notebook via GitHub Codespaces
          </p>
          <p><b>Dataset</b>:<br>
              Dataset was downloaded from <a href="https://rakamin-lms.s3.ap-southeast-1.amazonaws.com/vix-assets/idx-partners/loan_data_2007_2014.csv">Rakamin website</a></p><br>
        </div>
  
        <hr>

        <div id="prep" class="inner-content">
          <h4>Data Preprocessing and Cleaning</h4>
          <blockquote>These steps collectively ensure a clean and organized dataset, laying the groundwork for exploration and analysis while minimizing errors and ensuring data consistency.</blockquote>
          <img class="code" src="@/assets/images/projects/idx/code/dataprep.png">
        </div>

        <hr>

        <div id="initial" class="inner-content">
          <h4>Initial Data Finding</h4>
          <p>In the initial data exploration phase, various visualizations were created to better understand key aspects of the loan dataset. These visualizations collectively contribute to the initial understanding of key features within the dataset, laying the foundation for further analysis and insights in the data analysis process.</p>
          <img class="code" src="@/assets/images/projects/idx/code/initial_finding.png">
          <img class="code" src="@/assets/images/projects/idx/code/loan_grade_dist.png">
          <img class="hero" src="@/assets/images/projects/idx/plot/loan_grade.png">
          <img class="code" src="@/assets/images/projects/idx/code/loanamnt_loanstatus.png">
          <img class="hero" src="@/assets/images/projects/idx/plot/loanamnt_loanstatus.png">
          <img class="code" src="@/assets/images/projects/idx/code/intrates_loanstatus.png">
          <img class="hero" src="@/assets/images/projects/idx/plot/intrates_loanstatus.png">
          <img class="code" src="@/assets/images/projects/idx/code/anninc_dti.png">
          <img class="hero" src="@/assets/images/projects/idx/plot/anninc_dti.png">
        </div>

        <hr>

        <div id="feature" class="inner-content">
          <h4>Feature Engineering</h4>
          <p>Creating new features or modifying existing ones to to gain better insights from the data.</p>
          <img class="code" src="@/assets/images/projects/idx/code/feature_engineering.png">
        </div>

        <hr>

        <div id="in-depth" class="inner-content">
          <h4>In-Depth Analysis and Visualizations</h4>
          <img class="code" src="@/assets/images/projects/idx/code/loan_incratio.png">
          <img class="hero" src="@/assets/images/projects/idx/plot/loan_incratio.png">
          <img class="code" src="@/assets/images/projects/idx/code/loan_rates_issuance.png">
          <img class="code" src="@/assets/images/projects/idx/plot/loan_rates_issuance.png">
          <blockquote>The most noticeable insight is that in 2014, there was a significant increase in loan issuances, particularly in October, where over 38,000 loans were issued. This suggests a surge in lending activity during that specific month and year. possibly indicating a strategic move by the lending institution to boost lending during that period. Interestingly, the heatmap shows that the default rates were highest in the years 2011 and 2012, suggesting that loans issued during these periods were more likely to default. The variation in default rates across different years highlights potential patterns or trends that may influence credit risk and loan performance.</blockquote>
          <br>
          <img class="code" src="@/assets/images/projects/idx/code/loan_term.png">
          <img class="code" src="@/assets/images/projects/idx/plot/loan_term.png">
          <blockquote>The bar chart and pie chart collectively reveal that the majority of loans in the dataset have a 36-month term, constituting a substantial portion of the loan portfolio. Conversely, the 60-month term, while still popular, represents a smaller proportion of the total loans.</blockquote>
          <br>
          <img class="code" src="@/assets/images/projects/idx/code/intrates_average.png">
          <img class="hero" src="@/assets/images/projects/idx/plot/intrates_average.png">
          <img class="code" src="@/assets/images/projects/idx/code/corr_analysis.png">
          <img class="code" src="@/assets/images/projects/idx/plot/corr_analysis.png">
          <p>
            Strong positive correlations:
              <li> loan_amnt and funded_amnt (0.99): This is to be expected, as the funded amount is typically a portion of the loan amount requested. </li>
              <li> annual_inc and loan_amnt (0.37): Borrowers with higher incomes tend to take out larger loans. </li>
              <li> total_acc and open_acc (0.67): Borrowers with more open accounts also tend to have more total accounts. </li>
              <li> loan_term and int_rate_diff (0.44): Borrowers with longer loan terms tend to have higher interest rate differences compared to the average. </li><br>
            Strong negative correlations:
              <li> dti and annual_inc (-0.67): Borrowers with higher debt-to-income ratios tend to have lower incomes. </li>
              <li> dti and credit_util_ratio (-0.40): Borrowers with higher debt-to-income ratios also tend to have lower credit utilization ratios. </li>
              <li> int_rate and dti_ratio (-0.29): Borrowers with higher debt-to-income ratios tend to have lower interest rates. </li><br>
            Weak correlations:
              <li> loan_status_binary with most other features: This suggests that loan status is not strongly related to most of the other features in the dataset. </li>
              <li> issue_month with most other features: This suggests that the month in which the loan was issued is not strongly related to most of the other features in the dataset. </li>
          </p>
          <br>
          <img class="code" src="@/assets/images/projects/idx/code/10_states_loans.png">
          <img class="hero" src="@/assets/images/projects/idx/plot/10_states_loans.png">
          <img class="code" src="@/assets/images/projects/idx/code/choropleth.png">
          <iframe src="https://zulfikawr.github.io/idx_choropleth/"/>
          <blockquote>
            The map reveals that California (CA) has the highest number of loans, with over 70,000 loans. New York (NY) follows with around 40,000 loans, and Texas (TX) is close behind with approximately 36,000 loans.
          </blockquote>
        </div>

        <hr>

        <div id="suggestions" class="inner-content">
          <h4>Recommendations</h4>
          <p>This section provides a series of strategic suggestions to improve business based on the findings from the data analysis of a loan dataset.</p>
          <p><li>Focus on 36-Month Terms:</li>
    
              The majority of loans in the dataset have a 36-month term. Consider continuing to offer and promote these shorter-term loans, as they are more popular among borrowers.<br><br>
    
          <li>Strategic Issuance in High-Performing Months:</li>
              
              Analyze the factors contributing to the surge in loan issuances in specific months, such as the notable increase in October 2014. Consider replicating successful strategies during those high-performing months.<br><br>
              
          <li>Manage Default Rates:</li>
              
              Address the higher default rates observed in 2011 and 2012. Evaluate the underwriting criteria during those periods and identify any patterns or risk factors contributing to increased default rates. Implement strategies to mitigate default risks.<br><br>
              
          <li>Diversify Marketing Strategies:</li>
              
              Explore and diversify marketing strategies to attract a broader customer base. Understand the preferences and characteristics of borrowers with successful repayment histories and target similar demographics.<br><br>
              
          <li>Optimize Interest Rates:</li>
              
              Analyze the distribution of interest rates and their impact on loan performance. Consider optimizing interest rates to remain competitive while ensuring profitability and managing default risks.<br><br>
              
          <li>Enhance Geographic Presence:</li>
              
              Assess the geographic distribution of loans and identify regions with high demand. Consider expanding or refining the company's presence in those areas to tap into potential markets.<br><br>
              
          <li>Customer Education and Transparency:</li>
              
              Enhance customer education regarding loan terms, interest rates, and repayment processes. Transparency in communication can build trust and improve customer satisfaction.<br><br>
              
          <li>Adapt to Economic Conditions:</li>
              
              Stay vigilant to economic conditions that may impact borrower repayment capabilities. Develop adaptive strategies to navigate economic fluctuations and minimize the impact on loan performance.<br><br>
              
          <li>Continuous Monitoring and Adaptation:</li>
              
              Establish a robust monitoring system to track key performance indicators over time. Regularly revisit and adapt business strategies based on evolving market conditions and customer behaviors.<br><br>
              
          <li>Optimize Current Loan Portfolio:</li>
              
              Since a significant portion of loans is labeled as "Current," focus on optimizing the management and servicing of these loans. Implement strategies to minimize the risk of loans transitioning into delinquency.<br><br>
              
          <li>Customer Engagement for Fully Paid Loans:</li>
              
              For loans labeled as "Fully Paid," leverage this positive outcome to engage with customers. Consider soliciting feedback, offering loyalty incentives for repeat business, and encouraging satisfied customers to refer others.<br><br>
              
          <li>Mitigate Risk for Delinquent Loans:</li>
              
              Given the lower frequencies in other loan statuses, pay special attention to loans with delinquent statuses. Implement proactive measures such as targeted communication, flexible repayment plans, or refinancing options to mitigate the risk of default.<br><br>
              
          <li>Enhance Communication Strategies:</li>
              
              Improve communication strategies for borrowers across different loan statuses. Provide clear and transparent communication regarding payment schedules, outstanding balances, and any available support or resources in case of financial difficulties.<br><br>
              
          <li>Customized Marketing for Different Loan Statuses:</li>
              
              Tailor marketing efforts based on the loan status. For instance, develop campaigns to encourage borrowers with fully paid loans to consider additional financial products or services. For borrowers with delinquent status, provide resources to help them get back on track.<br><br>
              
          <li>Implement Predictive Analytics:</li>
              
              Utilize predictive analytics to forecast the likelihood of loans transitioning into different statuses. This can aid in early intervention strategies for loans showing signs of potential issues.<br><br>
              
          <li>Customer Retention Programs:</li>
              
              Design customer retention programs for borrowers with fully paid loans to foster long-term relationships. Offer exclusive benefits, promotions, or loyalty programs to incentivize them to choose the company for future financial needs.<br><br>
              
          <li>Diversify Loan Products:</li>
              
              Explore diversification of loan products to attract a wider range of customers. Different loan products may appeal to various segments of the market, potentially reducing the concentration of loans in the "Current" status.<br><br>
          </p>
        </div>

    </div>
  </template>

  
<script>
export default {
  methods: {
    scrollToSection(sectionId) {
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({
          behavior: 'smooth',
          block: 'start',
        });
      }
    },
  },
};
</script>

<style scoped>
.hero {
  width: 100%;
  background-position: center center;
  background-size: 100%;
  background-repeat: no-repeat;
  border: 1px solid rgb(0, 0, 0, 0.1);
  margin-bottom: 15px;
}

.images {
  width: 100%;
  height: 350px;
  /* object-fit: cover; */
}

.images-full {
  width: 100%;
  height: auto;
  object-fit: cover;
}

.subtitle {
  font-size: 14px;
  color: gray;
  text-align: center;
}

.heading {
  padding-bottom: 5px;
}

.inner-content {
  padding-top: 30px;
  padding-bottom: 30px;
}

.code {
  width: 100%;
}

h6,
h3 {
  margin: 0;
  padding: 0;
  text-align: center;
}

p {
  text-align: justify;
  font-size: 15px;
  font-weight: normal;
}

iframe{
  width: 100%;
  height: 275px;
}

a {
  font-size: 15px;
  color: rgba(0, 0, 0, 0.918);
  text-decoration: underline;
}

.link {
  color: none;
  text-decoration: none;
  font-weight: normal;
  cursor: pointer;
}

.badge-grid {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 5px;
  margin-bottom: 20px;
}

.badge {
  width: auto;
  height: 20px;
  border-radius: 0px;
  font-size: 12px;
  padding-right: 10px;
}

blockquote {
  border-left: 2px solid rgba(10, 10, 10, 0.815);
  padding-left: 8px;
  text-align: justify;
  font-size: 13;
}

li {
  list-style: square;
}

.table-of-contents li {
  margin-bottom: 5px;
}

.table-of-contents a {
  text-decoration: none;
  color: blue;
}

.table-of-contents a:hover {
  text-decoration: underline;
}

</style>