# ParzenWindow
Performing **non-parametric Parzen Window estimation** on the '[ted_main.csv](https://github.com/fardinabbasi/ParzenWindow/blob/main/ted_main.csv)' dataset, both **from scratch** and using **built-in** functions.
The duration column of the dataset is extracted to estimate its **distribution** using **Parzen Window** with **Gaussian kernel**.
## From Scratch
Here is the implementation of the **Parzen Window with Gaussian kernel** from scratch.
```ruby
def ParzenWindow_est(x,x_samples,h):
	k=0
	for xi in x_samples:
		k += norm.pdf((x-xi)/h,loc=0,scale=1)
	p=k/(len(x_samples)*h)
	return p
```
Below are the results of the distribution estimation for various **window widths (*h*)**.
| *h* | 10 | [20, 50, 100] |
| --- | --- | --- |
| Estimation | <img src="./doc/h10.png"> | <img src="./doc/h.png"> |

Window width (*h*) is also known as the **smoothing factor**. As you can observe, increasing h leads to a smoother distribution.

## With Built-in Functions
```ruby
from sklearn.neighbors import KernelDensity
```
The table below displays the sample set sizes, ranging from 250 samples to the entire dataset, with increments of 250.
| 10% of the Dataset | 20% of the Dataset | 29% of the Dataset | 39% of the Dataset | 49% of the Dataset | 
| --- | --- | --- | --- | --- |
| <img src="./doc/n10.png"> | <img src="./doc/n20.png"> | <img src="./doc/n29.png"> | <img src="./doc/n39.png"> | <img src="./doc/n49.png"> |
| **59% of the Dataset** | **69% of the Dataset** | **78% of the Dataset** | **88% of the Dataset** | **98% of the Dataset** |
| <img src="./doc/n59.png"> | <img src="./doc/n69.png"> | <img src="./doc/n78.png"> | <img src="./doc/n88.png"> | <img src="./doc/n98.png"> |

It can be inferred that the larger the sample set, the **smoother** the distribution becomes, eventually **converging** to the actual distribution.

## Course Description
- **Course**: Machine Learning [ECE 501]
- **Semester**: Spring 2023
- **Institution:** [School of Electrical & Computer Engineering](https://ece.ut.ac.ir/en/), [College of Engineering](https://eng.ut.ac.ir/en), [University of Tehran](https://ut.ac.ir/en)
- **Instructors:** Dr. A. Dehaqani, Dr. Tavassolipour
