# Sentiment_Analysis
A sentiment analysis project that categorizes text into positive, negative sentiments through the application of Prompt Engineering methodologies.
# Software&tools
[GithhubAccount]

[VSCodeIDE]

[AzureOpenAILab]

# **Business Overview:**

ExpressWay Logistics is a dynamic logistics service provider, committed to delivering efficient, reliable and cost-effective courier transportation and warehousing solutions. With a focus on speed, precision and customer satisfaction, we aim to be the go-to partner for our customers seeking seamless courier services. Our core service involves ensuring operational efficiency throughout our delivery and courier services, including inventory management, durable packaging and swift dispatch of couriers, real time tracking of shipments and on-time delivery of couriers as promised. We are committed to enhance our logistics and courier services and improve seamless connectivity for our customers.
# **Current Challenge:**

ExpressWay Logistics faces numerous challenges in ensuring seamless deliveries and customer satisfaction. These challenges include managing various customer demands simultaneously, addressing delays in deliveries and ensuring products arrive intact and safe. Additionally, the company struggles with complexity of efficiently storing and handling a large volume of packages and ultimately meeting customer expectations. Moreover, maintaining a skilled workforce capable of handling various aspects of logistics operations presents its own set of challenges. Overcoming these obstacles requires a comprehensive approach that integrates innovative technology, strategic planning, and continuous improvement initiatives to ensure smooth operations and exceptional service delivery.
# **Objective:**

Our primary objective is to conduct a sentiment analysis of user-generated reviews across various digital channels and platforms. By paying attention to their feedback, we want to find ways to make our services better - like handling different customer demands simultaneously, dealing with late deliveries, and keeping packages secured and intact. Through the application of prompt engineering methodologies and sentiment analysis, we'll figure out if sentiments expressed by users for our courier services are Positive or Negative. This will help us understand where we need to improve in order to meet customer expectations and keep them happy. With a focus on getting better all the time, we'll overcome the challenges at ExpressWay Logistics and make our services the best.
# **Data Description:**

The dataset titled "courier-service_reviews.csv" is structured to facilitate sentiment analysis for courier service reviews. Here's a brief description of the data columns:

1. id: This column contains unique identifiers for each review entry. It helps in distinguishing and referencing individual reviews.
2. review: This column includes the actual text of the courier service reviews. The reviews are likely composed of customer opinions and experiences regarding different aspects of the services provided by ExpressWay Logistics.
3. sentiment: This column provides an additional layer of classification (positive and negative) for the mentioned reviews.
# Clone Repo using 
[git clone https://github.com/username/Sentiment_Analysis.git] at the folder location.
# !pip install openai==1.2 tiktoken datasets session-info --quiet
# Pip install all imports from Requirements.txt file.

# Authentication 
[Config.json] file that includes authentication required to acess AzureOpenAIAPI.

# Utilities
To count the no of tokens used.

# Task Sentiment Analysis
# Load the courier-service_reviews.csv file.
# Split the Dataset for train-test-split.

To select gold examples for this session, we sample randomly from the test data using a `random_state=42`. This ensures that the examples from multiple runs of the sampling are the same (i.e., they are randomly selected but do not change between different runs of the notebook). Note that we are doing this only to keep execution times low for illustration. In practise, large number of gold examples facilitate robust estimates of model accuracy.

# Load gold examples
Test an single sigle example and see the sentiment.

# Devise Prompt
provide User message template as {courier_service_review}
Write Zero Shot Message.
create Zero Shot prompt.

write Few Shot message which may be almost similar to Zero Shot message.
Create examples for Few Shot message.

With the examples in place, we can now assemble a few-shot prompt. Since we will be using the few-shot prompt several times during evaluation, let us write a function to create a few-shot prompt (the logic of this function is depicted below).

Create Few Shot Prompt.
"""
    Return a prompt message in the format expected by the Open AI API.
    Loop through the examples and parse them as user message and assistant
    message.

    Args:
        system_message (str): system message with instructions for sentiment analysis
        examples (str): JSON string with list of examples
        user_message_template (str): string with a placeholder for courier service reviews

    Output:
        few_shot_prompt (List): A list of dictionaries in the Open AI prompt format
    """
# Evaluate Prompts
Now we have two sets of prompts that we need to evaluate using gold labels. Since the few-shot prompt depends on the sample of examples that was drawn to make up the prompt, we expect some variability in evaluation. Hence, we evaluate each prompt multiple times to get a sense of the average and the variation around the average.

To reiterate, a choice on the prompt should account for variability due to the choice of the random sample. To aid repeated evaluation, we assemble an evaluation function .
Let us now use this function to do one evaluation of all the two prompts assembled so far, each time computing the Micro-F1 score.
# Evaluate Zero Shot Prompt
# Evaluate Few Shot Prompt
WE can see there is little/no difference in Evaluation by micro f1 score.
However, this is just *one* choice of examples. We will need to run these evaluations with multiple choices of examples to get a sense of variability in F1 score for the few-shot prompt. As an example, let us run evaluations for the few-shot prompt 5 times.
# Compute the average (mean) and measure the variability (standard deviation) of the evaluation scores for both zero shot and few shot prompts.
Observations and Learnings
Sentiment Analysis Insights:

Conducting sentiment analysis on user-generated reviews has revealed the overall perception of ExpressWay Logistics' services.
By categorizing reviews into positive and negative sentiments, we can identify specific strengths and weaknesses in our service offerings. And also the F1 score defines the readings of zero shot and few shot really doesn't make much difference and almost the same.

# Breakdown of Reviews:

This breakdown provides a clear picture of customer satisfaction and areas requiring attention.
Key Learnings:

Understanding customer sentiment helps pinpoint common themes in feedback, allowing for targeted improvements.
Recognizing trends in positive reviews can inform strategies for maintaining strengths, while negative feedback can highlight urgent areas for enhancement.

# Business Use Case

The insights gained from sentiment analysis can be directly beneficial to ExpressWay Logistics in several ways:

# Improving Customer Experience:

By addressing issues highlighted in negative reviews (e.g., late deliveries, damaged packages), the company can enhance its overall service quality.
Positive feedback can be leveraged in marketing efforts to build customer trust and brand reputation.

# Operational Efficiency:

Identifying recurrent themes in negative feedback can help streamline operations, whether it's optimizing delivery routes or improving packaging methods.
Understanding customer demands and pain points allows for better resource allocation and workforce management.

# Strategic Planning:

The sentiment classification aids in decision-making, guiding investments in technology and training to address gaps in service.
Continuous monitoring of sentiment can establish benchmarks for service improvements and measure progress over time.

# Customer Retention and Satisfaction:

By actively responding to and resolving issues raised in negative reviews, ExpressWay Logistics can foster loyalty and increase customer satisfaction.

A commitment to continuous improvement based on customer feedback demonstrates a customer-centric approach, further enhancing the company's reputation.

# Conclusion

In summary, leveraging sentiment analysis of customer reviews offers invaluable insights into ExpressWay Logistics’ operational strengths and weaknesses. By breaking down review sentiments and addressing identified challenges, the company can significantly improve its service delivery, enhance customer satisfaction, and maintain a competitive edge in the logistics industry.