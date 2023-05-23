
#### Step 1: NVIDIA Video Driver (Normal Gaming Driver)

You should install the latest version of your GPUs driver.


#### Step 2: Visual Studio, C++

After download while installing, go to Indivial Components
Then from compilers, build tools check All C++ Tools and MSBuild


#### Step 3: CUDA and CuDNN

CUDA Version - 11.2
CuDNN Version - 8.1


#### Step 4 : Unzip CuDNN to C:/tools

Unzip downloaded CuDNN zipped file to c:/tools.


#### Step 5: Add environment variables

```PATH 
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\extras\CUPTI\lib64
```

```PATH
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\extras\CUPTI\include
```

```PATH
C:\tools\cuda\bin
```

```PATH
C:\tools\cuda\include
```


#### Step 6: Install TensorFlow after creating environment

Install TensorFlow
```python
pip install tensorflow==2.10.0
```

#### Step 7: Verify if GPU is supports

Now check if everything is installed and setup properly (A slight version mismatch can cause error or not support GPU).

```Python
import tensorflow as tf
print(len(tf.config.list_physical_devices('GPU'))>0)
```

If the output is True, it mean tensorflow has successfully detected your GPU else please check for mistakes.






#python #ml #tensorflow