# new-word-probility
This python code applies _Probability of Acute Change Metric_ on Conversation Data to analyze probability of acute increase of new words in time-series conversation data.
The code is used to **analyze word use across time in group conversation data**. In particular, it examines the likelihood of forming or using new words at a certain time of point. The method is originally used to examine affective instability in Jahng et al., 2008 [Link](https://psycnet.apa.org/record/2008-17368-004) and applied in our paper below:

Ge, X., Leifer, L., & Shui, L. (2021). Situated emotion and its constructive role in collaborative design: A mixed-method study of experienced designers. Design Studies, 75, 101020. https://www.sciencedirect.com/science/article/pii/S0142694X21000314 


# What does the code do to calculate Probability of Acute Change?

The code take this input of conversation data:

<img width="1323" alt="Screen Shot 2021-11-02 at 5 12 15 PM" src="https://user-images.githubusercontent.com/733839/139968594-3fab92f4-7aef-41ca-be2c-0bfc455fab30.png">

And it produces necessary outputs for caculating the probability of acute change (PAC) through this process:

![image](https://user-images.githubusercontent.com/733839/139968744-a5d81c6d-1c01-49a2-ab36-b2d21e1b7216.png)



# Source of code
The code is writtend by Hao Zhong and Xiao Ge.

The code was built for data analysis in this paper: 

Ge, X., Leifer, L., & Shui, L. (2021). Situated emotion and its constructive role in collaborative design: A mixed-method study of experienced designers. Design Studies, 75, 101020. https://www.sciencedirect.com/science/article/pii/S0142694X21000314 

The example input data is from the above paper.

**Please cite if you were to use the code and our method.

