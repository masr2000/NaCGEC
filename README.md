# NLPCC2023 Shared Task 1: Chinese Grammatical Error Correction

## Task Introduction

Chinese Grammatical Error Correction (CGEC) aims to automatically correct grammatical errors that violate language rules and converts the noisy input texts to clean output texts. The widely used benchmarks are derived from the grammatical errors made by foreign Chinese learners (i.e., L2 learners). The gap between the language usage habits of L2 learners and Chinese native speakers makes the performance of the CGEC models in real scenarios unpredictable.  This task focuses on correcting grammatical errors made by Chinese native speakers, which will be a challenging benchmark and a meaningful resource to facilitate further development of CGEC.

## Updates

All updates about this shared task will be posted on this page.

- 2023/08/22：Ground truths of test data has been released.

- 2023/06/10：The leaderboard has been published.

- 2023/05/21：The input of test data has been released. The file is located at `data/nacgec.test.input`. Please note that the submission deadline is 2023/05/31.

- 2023/05/05：Registration has been closed. If you have already registered, please check the `Participants` list.

## Important Dates

- 2023/03/15：registration open
- 2023/04/06：release of detailed task guidelines & training data
- 2023/05/05：registration deadline
- 2023/05/21：release of test data
- 2023/05/31：participants’ results submission deadline
- 2023/06/10：evaluation results release and call for system reports and conference paper

## Leaderboard

<table>
<thead>
  <tr>
    <th rowspan="2">Rank</th>
    <th rowspan="2">System Name</th>
    <th colspan="3">MaxMatch</th>
    <th colspan="3">ChERRANT</th>
    <th rowspan="2">Score</th>
  </tr>
  <tr>
    <th>Precision</th>
    <th>Recall</th>
    <th>F0.5</th>
    <th>Precision</th>
    <th>Recall</th>
    <th>F0.5</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>1</td>
    <td>HW_TSC_nlpcc2023_cgec</td>
    <td>56.23</td>
    <td>33.3</td>
    <td>49.42</td>
    <td>50.95</td>
    <td>31.29</td>
    <td>45.26</td>
    <td>47.34</td>
  </tr>
  <tr>
    <td>2</td>
    <td>鱼饼啾啾Plus</td>
    <td>57.08</td>
    <td>12.94</td>
    <td>33.94</td>
    <td>54.5</td>
    <td>13.06</td>
    <td>33.34</td>
    <td>33.64</td>
  </tr>
  <tr>
    <td>3</td>
    <td>CUHK_SU</td>
    <td>38.82</td>
    <td>15.58</td>
    <td>29.9</td>
    <td>45.4</td>
    <td>15.15</td>
    <td>32.45</td>
    <td>31.175</td>
  </tr>
  <tr>
    <td>4</td>
    <td>CGEC++</td>
    <td>24.14</td>
    <td>7.35</td>
    <td>16.57</td>
    <td>21.11</td>
    <td>7.32</td>
    <td>15.33</td>
    <td>15.95</td>
  </tr>
  <tr>
    <td>5</td>
    <td>zhao_jia</td>
    <td>17.19</td>
    <td>14.78</td>
    <td>16.65</td>
    <td>13.51</td>
    <td>13.43</td>
    <td>13.49</td>
    <td>15.07</td>
  </tr>
  <tr>
    <td>6</td>
    <td>ZZUNLP</td>
    <td>4.31</td>
    <td>0.99</td>
    <td>2.58</td>
    <td>2.21</td>
    <td>0.59</td>
    <td>1.43</td>
    <td>2.005</td>
  </tr>
  <tr>
    <td>7</td>
    <td>YNU-Janko</td>
    <td>0.51</td>
    <td>6.36</td>
    <td>0.62</td>
    <td>0.93</td>
    <td>2.34</td>
    <td>1.06</td>
    <td>0.84</td>
  </tr>
</tbody>
</table>


## Data Description & Rules

We provide a CGEC benchmark named *NaCGEC*, which focuses on grammatical errors made by native Chinese speakers. In this task, the benchmark data is split into two parts: Validation and Test.

- Validation: `nacgec.dev.ref.para` (put in `data`) includes 500 sentences and corresponding correct sentences sampled from the original dataset. **The validation set can be utilized for model performance testing and hyper-parameter tuning, but it cannot be directly used for model training. Each line of `nacgec.dev.ref.para` contains one training sample, and the format of a line is `<id>\t<source>\t<target1>\t<target2>...\n`. If `<target1>` and `<source>` in a line are the same, the `<source>` does not contain grammatical errors.**
- Test: `nacgec.test.input` (also put in `data`) includes 5869 sentences that may contain grammatical errors. Participants should use CGEC model to detect and correct each sentence and output the correct sentence.

**For model training, only the data provided by [this link](https://cloud.tsinghua.edu.cn/f/9e46b10b52564736b0f3/) is allowed to be used as supervised data, i.e, parallel data, which includes [Lang8](http://tcci.ccf.org.cn/conference/2018/taskdata.php), [HSK](https://cloud.tsinghua.edu.cn/f/9e46b10b52564736b0f3/),  [CGED](https://github.com/blcuicall/cged_datasets), [MuCGEC](https://github.com/HillZhang1999/MuCGEC), [YACLC](https://github.com/blcuicall/YACLC) and [CTC2021](https://github.com/destwang/CTC2021), in this shared task. When using these data, please follow the rules set by the original data publisher.** Meanwhile, **for unsupervised data, any corpus publicly available on the web is allowed to be used.** Based on unsupervised data, participants can use any data augmentation methods, such as [our work](https://github.com/masr2000/CLG-CGEC) or other methods, to construct pseudo-parallel data for model training.

For more information related to this dataset, please refer to our paper: [Linguistic Rules-Based Corpus Generation for Native Chinese Grammatical Error Correction](https://arxiv.org/pdf/2210.10442.pdf). If there are any differences between the paper and this page, the content of this page should prevail.

## Submission & Evaluation

For submission, the following materials should be packaged as one `zip` file and sent to masr21@mails.tsinghua.edu.cn:

- Submission File: The output sentences should be written into one text file. **The format of submission file must be the same as the input file. Specifically, the submission file must contain the same number of lines as the input file, and each line is a correct sentence corresponding to the sentence in the input file.** we also provide a submission sample file to show the format. 
- Code: The code folder should contain all the codes of data augmentation, data processing, model training and model inference. 
- Document: 
  - **Data Description: The document needs to contain a brief description of supervised and unsupervised data used in the experiment, as well as the data augmentation methods for unsupervised data.**
  - **Sharing Link of Unsupervised Data: Unsupervised data used in the experiment should be uploaded to a cloud storage, i.e., net disk, and the sharing link should be included in the document.** It is not allowed to use data that violates the rules during model training.
  - **Code Reproduction Process: The submitted code may be checked and reproduced by us, so please briefly explain the process of reproducing the code in the document.** 

For evaluation, we employ both word-based metrics and char-based span-level metrics. **For word-based metrics, an output sentence should be segmented into words using [THULAC](https://github.com/thunlp/THULAC-Python) toolkit, and then we utilize [MaxMatch](https://github.com/nusnlp/m2scorer) ($\text{M}^2$) scorer to compute Precision, Recall and $\text{F}_{0.5}$ between the output sentence and gold edits. For char-based span-level metrics, we use [ChERRANT](https://github.com/HillZhang1999/MuCGEC) to obtain the evaluation results. The final score is the average of $\text{F}_{0.5}$ scores obtained by word-based and char-based metrics, i.e., $\text{score}=0.5\cdot\text{F}_{0.5}\text{(word)}+0.5\cdot\text{F}_{0.5}\text{(char)}$.**

The top 3 participating teams will be certificated by NLPCC and CCF-NLP.

## Participants

| Team ID | Organization                                                 | System Name           |
| ------- | ------------------------------------------------------------ | --------------------- |
| 1       | Natural language processing laboratory of zhengzhou university | ZZUNLP                |
| 2       | MOE Key Laboratory of Computational Linguistics, School of Computer Science, Peking University | CGEC先遣队            |
| 3       | NanKai University, College of Computer Science, DBIS         | NLP Beginner          |
| 4       | Harbin Institute of Technology, Shenzhen ; School of Computer Science and Technology ; HappyTrans@HITsz | HappyTrans            |
| 5       | School of Computer Science & Technology, Beijing Institute of Technology | zhao jia              |
| 6       | Wangxuan Institute of Computer Technology, Peking University | PKU-WICT              |
| 7       | 杭州十域科技有限公司                                         | jojolee               |
| 8       | 北京大学                                                     | 鱼饼啾啾Plus          |
| 9       | Beihang University                                           | BUAA NLP              |
| 10      | 上海哔哩哔哩科技有限公司                                     | chole                 |
| 11      | Beijing Normal University, School of Artificial Intelligence, The Language and Character Resources Research Center of Beijing Normal University | Lrt123                |
| 12      | Yunnan University                                            | YNU-HPCC              |
| 13      | Huawei Translation Services Center                           | HW_TSC_nlpcc2023_cgec |
| 14      | Zhongyuan University of Technology                           | zutnlp-wuyanbo        |
| 15      | Yunnan University                                            | YNU-Janko             |
| 16      | NLP, School of Computer Science and Technology, Soochow University & NLP, School of Data Science, The Chinese University of Hong Kong, Shenzhen | CUHK_SU               |
| 17      | Social Computing Lab , Southeast University                  | CGEC++                |
| 18      | State Key Lab of Communication Content Cognition, People’s Daily Online | cc414                 |
| 19      | Fudan University                                             | cisl-nlp              |
| 20      | Ant Group                                                    | Lastonestands         |
| 21      | School of Information Science and Technology, Guangdong University of Foreign Studies; School of Computer Science and Technology, Guangdong University of Technology | BERT 4EVER            |
| 22      | School of Data Science and Engineering, East China Normal University | GGBond                |
| 23      | Text Machine Translation Lab, Huawei Technologies Co., Ltd.  | HW-TSC                |

## Contact & Citation

If your publication employs our dataset, please cite the following article:

```\
@inproceedings{ma2022linguistic,
  title={Linguistic Rules-Based Corpus Generation for Native Chinese Grammatical Error Correction},
  author={Ma, Shirong and Li, Yinghui and Sun, Rongyi and Zhou, Qingyu and Huang, Shulin and Zhang, Ding and Yangning, Li and Liu, Ruiyang and Li, Zhongli and Cao, Yunbo and others},
  booktitle = {Findings of the Association for Computational Linguistics: EMNLP 2022},
  year={2022}
}
```

If you have any questions about this task, please email to masr21@mails.tsinghua.edu.cn (C.C. liyinghu20@mails.tsinghua.edu.cn, zheng.haitao@sz.tsinghua.edu.cn).
