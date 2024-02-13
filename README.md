# MAPLE (Bill Summarization, Tagging, Explanation)  
In this project, we generate summaries and category tags for of Massachusetts bills for [MAPLE Platform](https://www.mapletestimony.org/). The goal is to simplify the legal language and content to make it comprehensible for a broader audience (9th-grade comprehension level) by exploring different ML and LLM services.  

This repository contains a pipeline from taking bills from Massachusetts legislature, generating summaries and category tags leveraging different the Massachusetts General Law sections, creating a dashboard to display and save the generated texts, to deploying and integrating into MAPLE platform.

## Roadmap of Repository Directories
* [Documentation](https://github.com/vynpt/ml-maple-bill-summarization/tree/dev/Documentation):  
  ```Research.md```: our research on large language models and evaluation methods we planned to use for this project.  
  ```Documentation MAPLE.pdf```: includes detail operation of our model for future use and improvement.
  
* [EDA](https://github.com/vynpt/ml-maple-bill-summarization/tree/dev/EDA): the notebook ```eda.ipynb``` includes our work from scraping data that takes bills from MAPLE Swagger API, creating a dataframe to clean and process data, making visualizations to analyze data and explore characteristics of the dataset.
  
* [demoapp](https://github.com/vynpt/ml-maple-bill-summarization/tree/dev/demoapp):   
  ```demo_app.py```: contains the codes of the LLM - OpenAI service and webapp made using Streamlit. The webapp allows user to search for all bills. MGL sections text is extracted for all but ~1300 bills and is available for in 'Combined_MGL' column in all_bills_with_mgl.pq file (currently hosted on google drive due to it's large size).

  Both demo_app.py and demo_app_with_12bills.py generate bill category and tags (based on a given list) and summarize the bill text for 12 bills and all bills, respectively. We currently use vectorstore to split the MGL document into chunks for vectorstore storage and embeddings before injection into the prompt. However, we would like to test injecting the MGL sections directly into the prompt without using vectorstores as the operations through vectorstores are fuzzy (rely on similarity search). 

  Currently using 'gpt-4' model for to generate categories (with the generate_category() function) and using 'gpt-4-1106-preview' to generate summaries of the bills (with the generate_response() function)


  Other files: helper files to be imported in the above two Python app files.
  
* [Prompts Engineering](https://github.com/vynpt/ml-maple-bill-summarization/tree/dev/Prompts%20Engineering): ```prompts.md``` stores all prompts that we tested.
  
* [Tagging](https://github.com/vynpt/ml-maple-bill-summarization/tree/dev/Tagging): contains the list of categories and tags.
  
* [Deployment](https://github.com/vynpt/ml-maple-bill-summarization/tree/main/Deployment): contains the link of our Streamlit deployed webapp.   

## Ethical Implications
The dataset used for this project is fully open sourced and can be access through Mass General Laws API.   

Our team and MAPLE agree about putting disclaimer that this text is AI-generated.  

Although we make use of open source transformers to evaluate hallucination with Vectara, it is important to have experts and human evaluation to further maintain a trustworthy LLM system.

## Resources and Citation
* https://huggingface.co/docs/transformers/tasks/summarization 
* https://huggingface.co/vectara/hallucination_evaluation_model  
* https://github.com/vectara/hallucination-leaderboard  
* https://www.nocode.ai/llms-undesirable-outputs/  
* https://learn.deeplearning.ai/  
* https://blog.langchain.dev/espilla-x-langchain-retrieval-augmented-generation-rag-in-llm-powered-question-answering-pipelines/  

## Team Members
Vy Nguyen - Email: nptv1207@bu.edu   
Andy Yang - Email: ayang903@bu.edu   
Gauri Bhandarwar - Email: gaurib3@bu.edu    
Weining Mai - Email: weimai@bu.edu 
