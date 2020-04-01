## datawhale project issue

brief record and essence worth written down.

### Task 2 Data EDA

target:

familiar with the data-set

relation between datas

preparing for data-engineering

main-content:

data importing and visualization

outline of data(pd.describe(),pd.info())

NAN value and inconsistent value

distribute ofd ata

### task 3 feature engineering

main-content:

1.exception data

2.data normalization

3.data bucket

4.NAN-value process

5.Feature construction

6.Feature screening

7.PCA，LDA,ICA

useful functions:
df.groupby()
pd.cut()  for bucket
sklearn.preprocessing
pd.get_dummies()

### task 4 build model and hyper-parameter tunning

main-content:

1.linear-regression:

  feature requriement：
  
    change object-type data
    
    data of the same distribution
    
    no NAN value
    
    

  handle long-tail distribution
  
2.embedding feature-selection

  lasso regression(L1 regulation)
  
  ridge regression(L2 regulation)
  
  decision tree

3.hyper parameter-tunning

  beyes optimization
  
  grid search
  
  greedy 
  
 useful func:
 
 def reduce_mem_usage(df):
    """ iterate through all the columns of a dataframe and modify the data type
        to reduce memory usage.        
    """
    start_mem = df.memory_usage().sum() 
    print('Memory usage of dataframe is {:.2f} MB'.format(start_mem))
    
    for col in df.columns:
        col_type = df[col].dtype
        
        if col_type != object:
            c_min = df[col].min()
            c_max = df[col].max()
            if str(col_type)[:3] == 'int':
                if c_min > np.iinfo(np.int8).min and c_max < np.iinfo(np.int8).max:
                    df[col] = df[col].astype(np.int8)
                elif c_min > np.iinfo(np.int16).min and c_max < np.iinfo(np.int16).max:
                    df[col] = df[col].astype(np.int16)
                elif c_min > np.iinfo(np.int32).min and c_max < np.iinfo(np.int32).max:
                    df[col] = df[col].astype(np.int32)
                elif c_min > np.iinfo(np.int64).min and c_max < np.iinfo(np.int64).max:
                    df[col] = df[col].astype(np.int64)  
            else:
                if c_min > np.finfo(np.float16).min and c_max < np.finfo(np.float16).max:
                    df[col] = df[col].astype(np.float16)
                elif c_min > np.finfo(np.float32).min and c_max < np.finfo(np.float32).max:
                    df[col] = df[col].astype(np.float32)
                else:
                    df[col] = df[col].astype(np.float64)
        else:
            df[col] = df[col].astype('category')

    end_mem = df.memory_usage().sum() 
    print('Memory usage after optimization is: {:.2f} MB'.format(end_mem))
    print('Decreased by {:.1f}%'.format(100 * (start_mem - end_mem) / start_mem))
    return df
    
    
 

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/PJSSABER/datawhale_ML-datamining/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
