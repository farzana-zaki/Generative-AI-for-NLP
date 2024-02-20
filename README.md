# Generative-AI-for-NLP
# Project Name: Generative AI-powered Support Ticket Categorization

# Business Context
In today's dynamic business landscape, organizations are increasingly recognizing the pivotal role customer feedback plays in shaping the trajectory of their products and services. The ability to swiftly and effectively respond to customer input not only fosters enhanced customer experiences but also serves as a catalyst for growth, prolonged customer engagement, and the nurturing of lifetime value relationships.

As a dedicated Product Manager or Product Analyst, staying attuned to the voice of your customers is not just a best practice; it's a strategic imperative.
While your organization may be inundated with a wealth of customer-generated feedback and support tickets, your role entails much more than just processing these inputs. To make your efforts in managing customer experience and expectations truly impactful, you need a structured approach – a method that allows you to discern the most pressing issues, set priorities, and allocate resources judiciously.

One of the most effective strategies at your disposal as an organization is to harness the power of automated Support Ticket Categorization - done in the modern day using Large Language Models and Generative AI.

# Project Objective
Develop a Generative AI application using a Large Language Model to automate the classification and processing of support tickets. The application will aim to predict ticket categories, assign priority, suggest estimated resolution times, generate responses based on sentiment analysis, and store the results in a structured DataFrame.

# Observations and insights:
The aim of this project is to create a Generative AI application that can automate the processing and classification of support tickets using a Large Language Model. To achieve this, I have utilized Llama 2, which is a pre-trained and fine-tuned generative text model ranging from 7 billion to 70 billion parameters. Specifically, I have used the 13B fine-tuned model (llama-2-13b-chat.Q6_K.gguf, which is a 6-bit quantized version model) that is optimized for dialogue use cases, and I have converted it to the Hugging Face Transformers format.

To create a prompt for the technical assistant, I merged the support ticket text from the input CSV file with a system message. The system message contains detailed instructions and guidelines to help the technical assistant classify the support ticket text, generate tags, assign priority, suggest the expected time of arrival (ETA), and create a sentiment-based response in JSON format. The system message also includes a one-shot example to guide the technical assistant.

Next, a response text from the LLaMA model was generated using the lcpp_llm instance with the following parameters: max_tokens = 256, temperature = 0, top_p = 0.95, repeat_penalty = 1.2, top_k = 50, and echo = False.

The generated LLaMA response includes some additional text before the JSON format response for each ticket. Therefore, text trimming was performed from the generated LLaMA response to keep only the JSON response.

Next, I parsed the JSON data, extracted key-value pairs, and normalized and concatenated them (setting axis = 1) in the 'data' DataFrame to add the JSON response as 5 new columns (category, tags, priority, suggested ETA, and generated 1st response) in the 'data' DataFrame for better visualization.

# Business Recommendations:
The objective of the application is to simplify the management of support tickets by incorporating advanced tools that automate the classification and processing of incoming tickets. The Llama 2 application model uses generative capabilities to process support tickets efficiently and effectively, which reduces response time and minimizes error rates. Overall, this project is a significant step forward in supporting ticket management, leveraging state-of-the-art AI technologies to enhance a crucial business function.

To enhance the performance of the LLM models and adapt their outputs to the specific business requirements, fine-tuning the prompt with a few shot examples can be very helpful. Additionally, tweaking the parameters of the prompt, such as Temperature, Top K, Frequency Penalty, etc., is another way to modify the LLM's outputs according to the specific business needs.
