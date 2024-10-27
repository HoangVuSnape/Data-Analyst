# Revise Numpy matplotlib Pandas
## Author: Vu Snape

## Numpy
    - Creating numpy
        ** a = np.array([[1,2,3],[4,5,6]])
        ** np.array([1, 2, 3, 4], dtype ='float32')
        ** np.zeros([2, 4], dtype = int)
        ** np.ones([3, 4], dtype= float)
        ** np.full((3, 2), 22)
        ** np.arange(0, 23, 2)
        
    - Get elements in array
        b = np.array([22, 26, 28, 10, 1, 2, 3])
        print(b[:2])
        print(b[1:6:2]) 
    - Mathematic 
        ** np.subtract 
        ** np.mutiply
        ** np.sort
        ** np.where
        ** np.dot
        ** np.matmul
        ** np.transpose 
        ** np.linalg.solve

    - Matrix random
        ** np.random.random((4, 4))
        ** np.random.seed(0)
        ** np.random.randint(0, 10, (4,5)) 
        ** np.eye
        ** np.empty
        ** A.dot(B)
            A @ B
        ** np.linspace
            x = np.linspace(0, 10, 1000)

## Matplotlib
    - See available style in matplotlib
    **  plt.style.available
        plt.style.use('seaborn-darkgrid')
    - There are two types to display in matplotlib
    ** Pyplot API - quickly
    ** OOP API - advanced
    - Attention in plt
        In pylplot api - Example: 
            x = np.linspace(0, 10, 1000)
            plt.plot(x, np.sin(x), color = "blue", linestyle = "dashed", label = "sin(x)")
            ** x, y: input 
            ** color
            ** linestyle
            ** label
        * plt.title
        * plt.xlabel/ylabel
        * plt.xlim
        * plt.axis
        * plt.lengend

        In OOP api - Example: 
        fig, ax = plt.subplots(figsize = (5,5)) # figure size = wid and height of plt 
        ax.plot(x, y);
        ax.set(title= "A simple plot", xlabel="x-axis", ylabel= "y-axis");

        Or:
        names = ['vu', 'mai', 'hang']
        marks = [22, 28, 26]

        plt.figure(figsize=(9,3))

        plt.subplot(131)
        plt.bar(names, marks)

        plt.subplot(132)
        plt.scatter(names, marks)

    - Most common types of matplotlib plots
        * line
        * scatter
        * bar
            ** when data display dict(keys, values)
            ** vertical/horizontal (bar, barh) 
        * hist
            ** bins 
        * subplot() - have lots of plots. 
    ** Note:
        *** Size
        *** cmap
        *** alpha

## Pandas
    - Reading data: 
        ** pd.read_csv/excel
        ** in other sheet1, 2, 3 and use function to covert.
            *** df = pd.read_excel("stock_data.xlsx", "Sheet1", converters= {
            'people' : convert_people_cell,
            'eps' : covert_eps_cell
        })

    - Set index / reset
        ** df.set_index('day', inplace=True)
        ** df.reset_index(inplace=True)

    - covert dict to dataframe
        ** weather_data = [
            {'day': '1/1/2017', 'temperature': 32, 'windspeed': 6, 'event': 'Rain'},
            {'day': '1/2/2017', 'temperature': 35, 'windspeed': 7, 'event': 'Sunny'},
            {'day': '1/3/2017', 'temperature': 28, 'windspeed': 2, 'event': 'Snow'},
            
        ]
        df = pd.DataFrame(data=weather_data, columns=['day','temperature','windspeed','event']) 

    - Overview data
        ** df.head(5)
        ** df.tail
        ** df.shape
        ** df.info
        ** df.describe
            *** df.describe(include= "all")     #input all both string. default = numeric/number
        ** df.columns
        ** df.index
        ** sum
            revenue = df["total_price"].sum()
        ** type(column)
           type(df['event'])
            
    - Handle missing
        ** df.fillna(0) : covert na to 0
            *** method: ffill/bfill : font/before
        
        ** df.dropna(how = "all")   #all cols have empty values.
            *** df.dropna(thresh = 2) # drop if have 2 data empty.   

    - Concat 2 cols
        ** df = pd.concat([vn_weather, india_weather], ignore_index= True) 
        ** df = pd.concat([temperature_df, windSpeed], axis = 1)

    - Different loc vs iloc (row and index)
        ** df.loc[(df.quantity == 1) | (df.item_name == "Nantucket Nectar"), ['order_id', 'quantity', 'item_name']]

        ** df.iloc[[9]] # dataframe
            # type(df.iloc[9]) ## series

    - apply
        ** df.item_price = df.item_price.apply(lambda x : float(str(x).replace('$', '')))
            df.item_price.dtype

    - create new column
        ** df['total_price'] = df['quantity'] * df['item_price']

    - Group by and sort values
        ** c = df.groupby("item_name")["quantity"].sum()
        c.sort_values(ascending= False).head(5)

    - Unique value
        ** df.item_name.nunique()

    - Mathematic: max/min
    ** df['temperature'].min()
    
    - Pivot data
        ** df.pivot(index ="humidity", columns ="city")
        ** df.pivot_table(index = "city", columns = "date")        
    - Melt data 
        ** df1 = pd.melt(df, id_vars = ["day"], var_name= "city")



    

