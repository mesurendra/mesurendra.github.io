---
layout: post
mathjax: true
title: Visual Explanation of Bayes Rule
Date: 2017-02-10
Tags: Statistics, ML
---

Venn Diagram is one of the easiest ways to visualize the Bayes Rule. For that, I take a classical example of computing probability of cancer given the test result is positive.

### Anatomy of a Test

* 1% of women have breast cancer (and therefore 99% do not).
* 80% of mammograms detect breast cancer when it is there (and therefore 20% miss it).
* 9.6% of mammograms detect breast cancer when it’s not there (and therefore 90.4% correctly return a negative result).

#### Now suppose a person get a positive test result. What are the chances the person has cancer?
####  80%? 99%? 1%?

P(Cancer | Test is Positive ) = ??

It looks like the right hand side of Bayes Formula. COOL!!

---

###  Venn Diagram of cancer test information

![Bayes rule 1](/assets/img/bayes/bayes_rule_1.png){:class="img-responsive"}

Area representing women having cancer (C=1) : ![Bayes_cancer](/assets/img/bayes/cancer.png)


Probability of breast cancer P(C=1) =  1%

Probability of not having cancer P(C=0) = (100 - 1)% = 99 %


$$ \mbox{Having cancer and test also positive} = P(T \cap C) $$ ![cancer_identified](/assets/img/bayes/cancer_identified.png)

Area representing positive result (T) (saying the woman has cancer) P(T=1):
![positive_test](/assets/img/bayes/positive_test.png)

Hence, P(C=1|T=1) =
![cancer_given_test_true](/assets/img/bayes/cancer_given_test_true.png)

#### Visually problem is solved


---
### Using Bayes Formula

$$ P(C|T) = \frac{P(T|C)*P(C)}{P(T)} = \frac{P(T \cap C)} {P(T) }$$



### Using the areas to compute the  probability.

80% of women having cancer are identified by test P(T=1|C=1)
= 80% = ![test_true_given_cancer](/assets/img/bayes/test_true_given_cancer.png)

$P(T \cap C)$ = 80% of 1% = 0.8 * 0.01  = 0.008 = ![cancer_identified](/assets/img/bayes/cancer_identified.png)
$$ P(T=1) =  P(T=1 \cap C=0) +  P(T=1 \cap C=1) $$

= ![total_test_true](/assets/img/bayes/total_test_true.png)

= 0.09504 + 0.008 = 0.10304

Probability of cancer given test is positive $P(C=1|T= 1)$ = ![cancer_given_test_true](/assets/img/bayes/cancer_given_test_true.png)
= 0.008/  0.10304

= 0.0776 = **7.76%**


---

$$Posterior =\frac{\textrm{(Prior X Likelihood)}} {\textrm{Evidence}}$$

$$p(cancer=1|\textrm{test_result}=+)=\frac{p(\textrm{test_result}=+|cancer=1) * p(cancer=1)} {p(\textrm{test_result}=+)}$$

### References:

* <http://yudkowsky.net/rational/bayes>
* <https://betterexplained.com/articles/an-intuitive-and-short-explanation-of-bayes-theorem/>
