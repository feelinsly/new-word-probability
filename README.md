# new-word-probility
This python code applies _Probability of Acute Change Metric_ on Conversation Data to analyze probability of acute increase of new words in time-series conversation data.
The code is used to **analyze word use across time in group conversation data**. In particular, it examines the likelihood of forming or using new words at a certain time of point. The method is originally used to examine affective instability in Jahng et al., 2008 ([Link](https://psycnet.apa.org/record/2008-17368-004)) and applied in our paper below:

Ge, X., Leifer, L., & Shui, L. (2021). Situated emotion and its constructive role in collaborative design: A mixed-method study of experienced designers. Design Studies, 75, 101020. https://www.sciencedirect.com/science/article/pii/S0142694X21000314 


# What does the code do to calculate Probability of Acute Change?
The analysis process is summarized as follows:

![image](https://user-images.githubusercontent.com/733839/139968744-a5d81c6d-1c01-49a2-ab36-b2d21e1b7216.png)

The python code take an input of conversation data, such as:

<img width="1323" alt="Screen Shot 2021-11-02 at 5 12 15 PM" src="https://user-images.githubusercontent.com/733839/139968594-3fab92f4-7aef-41ca-be2c-0bfc455fab30.png">

And it would produce necessary outputs for caculating the probability of acute change (PAC).

Example output:
<img width="412" alt="Screen Shot 2021-11-02 at 4 41 09 PM" src="https://user-images.githubusercontent.com/733839/139969763-0500fdcd-fde9-47e9-9bcb-68083d5d9fa0.png">

Probability of Acute Change (PAC) represents the likelihood of acute changes across time, de ned by the number of acute changes divided by the total number of changes, which in our context is the acute increase of new words. The equation for iPAC
is:
<img width="230" alt="Screen Shot 2021-11-02 at 5 17 29 PM" src="https://user-images.githubusercontent.com/733839/139968854-40cd5353-f6f5-4299-a59a-84962f56c87a.png">

where AC_i(t) = 1 when y_i(t+1)- y_i(t) >= c, c is a predetermined cut point (i.e., threshold), and AC_i(t) = 0 otherwise.

Once you have the outputs from the code, you might want to transition to R to do the necessary data analysis:

```
#create PAC - probability of acute change  - function
pac_d_Id <- function(data_Id, c)
{
  data_Id_lag <- lag(data_Id,k=-1,na.pad = TRUE) #this creates the lag variable
  ac = ifelse((data_Id-data_Id_lag) >= c,1,0)  #this calculates the binary acute change (deals with NA)
  denominator<-(length(ac)-1)         #this computes the number of non-missing elements (denominator)
  pac <- sum(ac/denominator,na.rm=TRUE)     #this calculates the pac
  return(pac)
}
```
```
#applying this function:
pac_new_word=pac_d_Id(time_weighted_new_word_count_rescaled,c=0.1)
```

The cut point, c, could be chosen by sensitivity analysis and should be the same across all individuals for a potential between-person comparison (Jahng et al., 2008). 

For our paper, acute increases of new words in the participant's talking, as compared with his/her previous usage of words, indicates, what we call "change of design frame", or "evolution of design frame", or "frame adjustment". 


# Source of code
The code is written by Hao Zhong and Xiao Ge.

The code was built for data analysis in this paper: 

Ge, X., Leifer, L., & Shui, L. (2021). Situated emotion and its constructive role in collaborative design: A mixed-method study of experienced designers. Design Studies, 75, 101020. https://www.sciencedirect.com/science/article/pii/S0142694X21000314 

The example input data is from the above paper.

**Please cite if you were to use the code and our method.

