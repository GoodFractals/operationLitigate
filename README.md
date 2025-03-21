# Operation Litigate


Comparative Analysis of Large Language Models on Legal Examination Tasks

Anthony Borum
Abtech Technologies
03 March 2025
Lab Instructor: Bob Russell
Lab day: Friday

Abstract
In this experiment, the performance of three large language models (LLMs) was assessed 
using the February 2021 California BAR Exam. The models included a baseline LLM without any 
prompting, a prompted LLM, and a prompted and supervised fine-tuned LLM. Each model was 
evaluated over ten iterations to determine the average performance of each on a scale from 1-100.
The baseline model scored an average of 89.35/100, outperforming both the prompted model which scored 
87.86/100, and the supervised fine-tuned model with a score of 84.6/100. The results suggest that the 
baseline model's performance was superior to both others in terms of accuracy, while the prompted model 
required significantly more processing time, and the fine-tuned model, although faster, scored the lowest. 
These findings highlight the complexities and trade-offs involved in optimizing LLMs for specific tasks.

Introduction
The rise of large language models (LLMs) such as GPT-4o-mini has revolutionized many natural language 
processing tasks. This study aimed to explore the effects of prompting and supervised fine-tuning on the 
performance of LLMs using the California BAR Exam. The main question was whether prompting, or fine-
tuning could enhance the model's performance compared to a baseline unprompted model. The BAR Exam 
was chosen due to its complexity, and tangible evaluation criteria. The null hypothesis was that there would be 
no significant difference in performance between the models, while the alternative hypothesis suggested that
both prompting and fine-tuning would improve the results.

Materials and Methods
Three LLM configurations were tested: a baseline with no prompting, a model that was prompted using a 
~6,000 word prompt, and a supervised fine-tuned model with 120 lines of JSONL data along with an extra 
system prompt added in at runtime. The JSONL file for the SFT model was generated using the same 6,000 
word prompt translated into a JSONL file with 120 lines of code using the Simpliscale Fine Tuning Formatter 
(Cornelius, 2024). Each model was evaluated using the February 2021 California BAR Exam, which was also 
the benchmark for grading. The exam answers were graded by an LLM trained on both the February 2021 CA
BAR exam's answer key and grading criteria. No other model was given access to the 2021 answer key, but 
both models besides the baseline were trained on the February 2019 & February 2020 CA BAR exam
questions and answers. Each model underwent ten iterations of testing, with randomization applied to the 
order of testing after each iteration. Metrics such as average score, response time, and token usage were 
recorded for analysis.

Results
The baseline LLM achieved the highest average score of 89.35/100, with an average response time of 12,013 
milliseconds (Table 1). The prompted model scored slightly lower, with an average of 87.86/100, but had a 
significantly longer response time of 17,989 milliseconds (Table 3). The fine-tuned model scored the lowest at 
84.6/100 yet had the fastest response time of 8,341 milliseconds (Table 4). The data indicates that while 
prompting increased computational demand, it did not substantially improve accuracy over the baseline. In 
contrast, the fine-tuned model reduced computational time, but resulted in lower performance. Although
scoring less than the baseline model, the model that only used prompting utilized almost 100x as many input 
tokens (Table 3). This was due to the entire prompt needing to be stored in the system message in order to be 
accessed at runtime.

Discussion
The experiment demonstrated that the baseline LLM outperformed both the prompted and fine-tuned models in 
terms of accuracy. The prompted model, while close in score, incurred a much higher computational cost, 
indicating inefficiency in the prompting process. The fine-tuned model, despite being optimized for faster 
response times, failed to achieve a competitive accuracy. These results suggest that while prompting and fine-
tuning can be valuable, their implementation must be carefully balanced with computational efficiency to 
achieve optimal results in practice. Future research could explore more refined prompting techniques, or 
alternative fine-tuning strategies such as direct preference optimization (DPO) in order to enhance 
performance. The results also suggest that if the constraints of the experiment were to allow each model to be 
trained on the specific test questions and answers instead of past years, they would perform more accurately 
than the unprompted model taking the same test.

Conclusion
In conclusion, this study evaluated the performance of three different configurations of large language models 
on the California BAR Exam: a baseline model, a prompted model, and a prompted and fine-tuned model. The 
baseline model demonstrated the highest accuracy, indicating that in this specific context, additional prompting 
and fine-tuning did not enhance performance. The prompted model, while nearly matching the baseline in 
accuracy, required significantly more computational resources, which highlighted a trade-off between accuracy 
and efficiency due to compute requirements scaling quadratically with the length of the sequence (IBM 
Technologies, 2025). The fine-tuned model, although faster, did not achieve the desired accuracy, suggesting 
that the fine-tuning process may need further optimization. These findings underscore the complexity of 
enhancing LLM performance and the need for a balanced approach that considers both accuracy and 
computational efficiency. Future research should focus on refining prompting and adopting different fine-tuning
techniques to better focus the capabilities of large language models on complex tasks like the BAR Exam.

References

Nick Cornelius. (2024, October 8). Fine-Tuning ChatGPT made EASY (No Coding Required) [Video]. YouTube. https://www.youtube.com/watch?v=FrshQV0PRq4

IBM Technologies (2025, January 1). What is a Context Window? Unlocking LLM Secrets [Video]. YouTube. https://www.youtube.com/watch?v=-QVoIxEpFkM

Table 1. Exam Scores
Trials	      Model 1 (No Prompt)	    Model 2 (Prompt Only)	    Model 3 (Prompt + SFT)
Trial # 1	          88/100	                 90/100	                   79/100
Trial # 2	          90/100	                 88.4/100	                 89/100
Trial # 3	          91/100	                 87/100	                   85/100
Trial # 4	          88/100	                 92/100	                   88/100
Trial # 5	          92/100	                 90/100	                   80/100
Trial # 6	          87.5/100	               82/100	                   80/100
Trial # 7	          91/100	                 88.2/100	                 86/100
Trial # 8	          87/100	                 88/100	                   86/100
Trial # 9	          88.4/100	               85/100	                   85/100
Trial # 10	        90.6/100	               88/100	                   88/100
Average:	          89.35/100	               87.86/100	               84.6/100


Table 2. Model #1 (no prompt) analysis
       Model	            BAR Question	   Response Time	   Input Tokens Used     Output Tokens Used
Model #1 (No Prompt)	       1.1	         "12,527ms"	        450 tokens	            888 tokens
Model #1 (No Prompt)	       1.2	         "6,278ms"	        435 tokens	            537 tokens
Model #1 (No Prompt)	       2.1	         "9,304ms"	        512 tokens	            704 tokens
Model #1 (No Prompt)	       2.2	         "12,787ms"         517 tokens	            629 tokens
Model #1 (No Prompt)	       3	           "10,560ms"	        238 tokens	            668 tokens
Model #1 (No Prompt)	       4.1	         "12,190ms"         405 tokens	            771 tokens
Model #1 (No Prompt)	       4.2	         "8,281ms"	        360 tokens	            445 tokens
Model #1 (No Prompt)	       5.1	         "18,600ms"	        370 tokens	            715 tokens
Model #1 (No Prompt)	       5.2	         "17,590ms"	        371 tokens	            658 tokens
Average	null	                             "12,013ms"	        406 tokens	            668 tokens


Table 3. Model #2 (prompt only) analysis
        Model	             BAR Question	    Response Time	   Input Tokens Used	    Output Tokens Used
Model #2 (Prompt Only)	      1.1	            "21,984ms"	    "31,000 tokens"	          801 tokens
Model #2 (Prompt Only)	      1.2     	      "15,560ms"	    "30,900 tokens"	          638 tokens
Model #2 (Prompt Only)	      2.1	            "21,236ms"	    "31,000 tokens"	          875 tokens
Model #2 (Prompt Only)	      2.2	            "17,130ms"	    "31,000 tokens"	          846 tokens
Model #2 (Prompt Only)	      3	              "17,028ms"	    "30,700 tokens"	          723 tokens
Model #2 (Prompt Only)	      4.1	            "18,252ms"	    "30,900 tokens"	          889 tokens
Model #2 (Prompt Only)	      4.2	            "12,812ms"	    "30,800 tokens"	          556 tokens
Model #2 (Prompt Only)	      5.1	            "16,813ms"	    "30,900 tokens"	          763 tokens
Model #2 (Prompt Only)	      5.2	            "21,086ms"	    "30,900 tokens"	          784 tokens
Average	                     null	            "17,989ms"	    "30,900 tokens"	          763 tokens


Table 4. Model #3 (SFT + prompt) analysis
          Model             BAR Question	  Response Time	   Input Tokens Used	    Output Tokens Used
Model #3 (Prompt + SFT)	      1.1	           "8,506ms"	        "474 tokens"	          742 tokens
Model #3 (Prompt + SFT)	      1.2	           "7,343ms"	        "459 tokens"	          393 tokens
Model #3 (Prompt + SFT)	      2.1	           "9,074ms"	        "519 tokens"	          591 tokens
Model #3 (Prompt + SFT)	      2.2	           "12,633ms"	        "524 tokens"	          617 tokens
Model #3 (Prompt + SFT)	       3	           "5,963ms"	        "254 tokens"	          372 tokens
Model #3 (Prompt + SFT)	      4.1	           "6,769ms"	        "421 tokens"	          414 tokens
Model #3 (Prompt + SFT)	      4.2	           "7,773ms"	        "376 tokens"	          263 tokens
Model #3 (Prompt + SFT)       5.1	           "7,868ms"	        "386 tokens"	          301 tokens
Model #3 (Prompt + SFT)	      5.2	           "9,139ms"	        "387 tokens"	          366 tokens
Average	                     null	           "8,341ms"	        "422 tokens"	          451 tokens
