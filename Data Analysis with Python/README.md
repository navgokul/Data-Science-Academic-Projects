<h1 align=center><font size = 6>Data Analysis with Python</font></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="(Project-Automobile-Dataset)">(Project-Automobile Dataset)<a class="anchor-link" href="#(Project-Automobile-Dataset)">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="1.-Introduction">1. Introduction<a class="anchor-link" href="#1.-Introduction">&#182;</a></h2><h4>We are estimating the price of a used car based on its characteristics?</h4><p>To answer this question, we are going to use various Python packages to perform data cleaning, exploratory data analysis, model development and model evaluation</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Table-of-content">Table of content<a class="anchor-link" href="#Table-of-content">&#182;</a></h2><div class="alert alert-block alert-info" style="margin-top: 20px">
1. Introduction<br>
    1.1 Data Acquisition<br>
    1.2 Basic Insight of Dataset<br>
2. Data Wrangling<br>
    2.1 Identify and handle missing values<br>
        2.1.1 Identify missing values<br>
        2.1.2 Deal with missing values<br>
        2.1.3 Correct data format<br>
    2.2 Data standardization<br>
    2.3 Data Normalization (centring/scaling)<br>
    2.4 Binning<br>
    2.5 Indicator variable<br>
3. Exploratory Data Analysis<br>
    3.1 Analyzing Individual Feature Patterns using Visualization<br>
    3.2 Categorical variables<br>
    3.3 Descriptive Statistical Analysis<br>
    3.4 Basic of Grouping<br>
    3.5 Correlation and Causation<br>
    3.6 ANOVA<br>
4. Model Development<br>
    4.1 Linear Regression and Multiple Linear Regression<br>
    4.2 Model Evaluation using Visualization<br>
        4.2.1 Regression Plot<br>
        4.2.2 Residual Plot<br>
        4.2.3 Multiple Linear Regression<br>
    4.3 Polynomial Regression and Pipelines<br>
        4.3.1 Pipeline<br>
    4.4 Measures for In-Sample Evaluation<br>
        4.1.1 R-squared<br>
        4.4.2 Mean Squared Error (MSE)<br>
    4.5 Prediction and Decision Making<br>
5. Model Evaluation and Refinement<br>
    5.1 Training and Testing<br>
    5.2 Overfitting, Underfitting and Model Selection<br>
    5.3 Ridge regression<br>
    5.4 Grid Search<br>
</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref1"></a></p>
<h2 id="1.1-Data-Acquisition">1.1 Data Acquisition<a class="anchor-link" href="#1.1-Data-Acquisition">&#182;</a></h2><p>There are various formats for a dataset, .csv, .json, .xlsx  etc. The dataset can be stored in different places, on your local machine or sometimes online.
In this section, you will learn how to load a dataset into our Jupyter Notebook.
In our case, the Automobile Dataset is an online source, and it is in CSV (comma separated value) format. Let's use this dataset as an example to practice data reading.
data source: <a href="https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data">https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data</a>
data type: csv
The Pandas Library is a useful tool that enables us to read various datasets into a data frame; our Jupyter notebook platforms have a built-in <strong>Pandas Library</strong> so that all we need to do is import Pandas without installing.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># import pandas library</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Read-Data">Read Data<a class="anchor-link" href="#Read-Data">&#182;</a></h3><p>We use <strong>"pandas.read_csv()"</strong>  function to read the csv file. In the bracket, we put the file path along with a quotation mark, so that pandas will read the file into a data frame from that address. The file path can be either an URL or your local file address.
Because the data does not include headers, we can add an argument <strong>" headers = None"</strong>  inside the  <strong>"read_csv()"</strong> method, so that pandas will not automatically set the first row as a header.
You can also assign the dataset to any variable you create.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># import pandas library</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="c1"># read the online file by the URL provides above, and assign it to variable &quot;df&quot;</span>
<span class="n">path</span><span class="o">=</span><span class="s2">&quot;https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data&quot;</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="n">path</span><span class="p">,</span><span class="n">header</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Done&quot;</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>After reading the dataset, we can use the <strong><code>dataframe.head(n)</code></strong> method to check the top n rows of the dataframe; where n is an integer. Contrary to <strong><code>dataframe.head(n)</code></strong>, <strong><code>dataframe.tail(n)</code></strong> will show you the bottom n rows of the dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># show the first 5 rows using dataframe.head() method</span>
<span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-1:-check-the-bottom-10-rows-of-data-frame-&quot;df&quot;.">Question 1: check the bottom 10 rows of data frame "df".<a class="anchor-link" href="#Question-1:-check-the-bottom-10-rows-of-data-frame-&quot;df&quot;.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">tail</span><span class="p">(</span><span class="mi">10</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Add-Headers">Add Headers<a class="anchor-link" href="#Add-Headers">&#182;</a></h3><p>Take a look at our dataset; pandas automatically set the header by an integer from 0.</p>
<div>
To better describe our data we can introduce a header, this information is available at:  https://archive.ics.uci.edu/ml/datasets/Automobile</div>
<p></p>
<div>Thus, we have to add headers manually.</div>
<div>Firstly, we create a list "headers" that include all column names in order.</div>
<div>Then, we use **`dataframe.columns = headers`** to replace the headers by the list we created.</div>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># create headers list</span>
<span class="n">headers</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;symboling&quot;</span><span class="p">,</span><span class="s2">&quot;normalized-losses&quot;</span><span class="p">,</span><span class="s2">&quot;make&quot;</span><span class="p">,</span><span class="s2">&quot;fuel-type&quot;</span><span class="p">,</span><span class="s2">&quot;aspiration&quot;</span><span class="p">,</span> <span class="s2">&quot;num-of-doors&quot;</span><span class="p">,</span><span class="s2">&quot;body-style&quot;</span><span class="p">,</span>
         <span class="s2">&quot;drive-wheels&quot;</span><span class="p">,</span><span class="s2">&quot;engine-location&quot;</span><span class="p">,</span><span class="s2">&quot;wheel-base&quot;</span><span class="p">,</span> <span class="s2">&quot;length&quot;</span><span class="p">,</span><span class="s2">&quot;width&quot;</span><span class="p">,</span><span class="s2">&quot;height&quot;</span><span class="p">,</span><span class="s2">&quot;curb-weight&quot;</span><span class="p">,</span><span class="s2">&quot;engine-type&quot;</span><span class="p">,</span>
         <span class="s2">&quot;num-of-cylinders&quot;</span><span class="p">,</span> <span class="s2">&quot;engine-size&quot;</span><span class="p">,</span><span class="s2">&quot;fuel-system&quot;</span><span class="p">,</span><span class="s2">&quot;bore&quot;</span><span class="p">,</span><span class="s2">&quot;stroke&quot;</span><span class="p">,</span><span class="s2">&quot;compression-ratio&quot;</span><span class="p">,</span><span class="s2">&quot;horsepower&quot;</span><span class="p">,</span>
         <span class="s2">&quot;peak-rpm&quot;</span><span class="p">,</span><span class="s2">&quot;city-mpg&quot;</span><span class="p">,</span><span class="s2">&quot;highway-mpg&quot;</span><span class="p">,</span><span class="s2">&quot;price&quot;</span><span class="p">]</span>
<span class="n">headers</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We replace headers and recheck our data frame</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="n">headers</span>
<span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">10</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we can drop missing values along the column "price" as follows</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">subset</span><span class="o">=</span><span class="p">[</span><span class="s2">&quot;price&quot;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now, we have successfully read the raw dataset and add the correct headers into the data frame.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-2:Find-the-name-of-the-colunms-of-the-dataframe">Question 2:Find the name of the colunms of the dataframe<a class="anchor-link" href="#Question-2:Find-the-name-of-the-colunms-of-the-dataframe">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">columns</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Save-Dataset">Save Dataset<a class="anchor-link" href="#Save-Dataset">&#182;</a></h3><p>Correspondingly, Pandas enables us to save the dataset to csv  by using the <strong><code>dataframe.to_csv()</code></strong> method, you can add the file path and name along with quotation marks in the brackets.</p>
<p>For example, if you would save the dataframe "df" as "automobile.csv" to your local machine, you may use the syntax below:</p>

<pre><code>df.to_csv("automobile.csv")</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can also read and save other file formats, we can use similar functions to <strong><code>pd.read_csv()</code></strong> and <strong><code>df.to_csv()</code></strong> for other data formats, the functions are listed in the following table:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Read/Save-Other-Data-Formats">Read/Save Other Data Formats<a class="anchor-link" href="#Read/Save-Other-Data-Formats">&#182;</a></h3><table>
<thead><tr>
<th>Data Formate</th>
<th style="text-align:center">Read</th>
<th style="text-align:right">Save</th>
</tr>
</thead>
<tbody>
<tr>
<td>csv</td>
<td style="text-align:center"><code>pd.read_csv()</code></td>
<td style="text-align:right"><code>df.to_csv()</code></td>
</tr>
<tr>
<td>json</td>
<td style="text-align:center"><code>pd.read_json()</code></td>
<td style="text-align:right"><code>df.to_json()</code></td>
</tr>
<tr>
<td>excel</td>
<td style="text-align:center"><code>pd.read_excel()</code></td>
<td style="text-align:right"><code>df.to_excel()</code></td>
</tr>
<tr>
<td>hdf</td>
<td style="text-align:center"><code>pd.read_hdf()</code></td>
<td style="text-align:right"><code>df.to_hdf()</code></td>
</tr>
<tr>
<td>sql</td>
<td style="text-align:center"><code>pd.read_sql()</code></td>
<td style="text-align:right"><code>df.to_sql()</code></td>
</tr>
<tr>
<td>...</td>
<td style="text-align:center">...</td>
<td style="text-align:right">...</td>
</tr>
</tbody>
</table>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref2"></a></p>
<h2 id="1.2-Basic-Insight-of-Dataset">1.2 Basic Insight of Dataset<a class="anchor-link" href="#1.2-Basic-Insight-of-Dataset">&#182;</a></h2><p>After reading data into Pandas dataframe, it is time for us to explore the dataset.
There are several ways to obtain essential insights of the data to help us better understand our dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Data-Types">Data Types<a class="anchor-link" href="#Data-Types">&#182;</a></h3><p>Data has a variety of types.
The main types stored in Pandas dataframes are <code>object</code>, <code>float</code>, <code>int</code>, <code>bool</code> and <code>datetime64</code>. In order to better learn about each attribute, it is always good for us to know the data type of each column. In Pandas:</p>

<pre><code>dataframe.dtypes</code></pre>
<p>returns a Series with the data type of each column.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># check the data type of data frame &quot;df&quot; by .dtypes</span>
<span class="n">df</span><span class="o">.</span><span class="n">dtypes</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As a result, as shown above, it is clear to see that the data type of "symboling" and "curb-weight" are <code>int64</code>, "normalized-losses" is <code>object</code>, and "wheel-base" is <code>float64</code>, etc.
These data types can be changed; we will learn how to accomplish this in a later module.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Describe">Describe<a class="anchor-link" href="#Describe">&#182;</a></h3><p>If we would like to get a statistical summary of each column, such as  count, column mean value, column standard deviation, etc. We use the describe method:</p>

<pre><code>dataframe.describe()</code></pre>
<p>This method will provide various summary statistics, excluding <code>NaN</code> (Not a Number) values.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This shows the statistical summary of all numeric-typed (int, float) columns.
For example, the attribute "symboling" has 205 counts, the mean value of this column is 0.83, the standard deviation is 1.25, the minimum value is -2, 25th percentile is 0, 50th percentile is 1, 75th percentile is 2, and the maximum value is 3.</p>
<p>However, what if we would also like to check all the columns including those that are of type object.</p>
<p>You can add an argument <code>include = "all"</code> inside the bracket. Let's try it again.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># describe all the columns in &quot;df&quot; </span>
<span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">(</span><span class="n">include</span> <span class="o">=</span> <span class="s2">&quot;all&quot;</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now, it provides the statistical summary of all the columns, including object-typed attributes.
We can now see how many unique values, which is the top value and the frequency of top value in the object-typed columns.
Some values in the table above show as "NaN", this is because those numbers are not available regarding a particular column type.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-3:-Apply-the--method-to-&quot;.describe()&quot;-to-the-columns-'length'-and-'compression-ratio'.">Question 3: Apply the  method to ".describe()" to the columns 'length' and 'compression-ratio'.<a class="anchor-link" href="#Question-3:-Apply-the--method-to-&quot;.describe()&quot;-to-the-columns-'length'-and-'compression-ratio'.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;length&#39;</span><span class="p">,</span> <span class="s1">&#39;compression-ratio&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Info">Info<a class="anchor-link" href="#Info">&#182;</a></h3><p>Another method you can use to check your dataset is:</p>

<pre><code>dataframe.info</code></pre>
<p>It provide a concise summary of your DataFrame.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># look at the info of &quot;df&quot;</span>
<span class="n">df</span><span class="o">.</span><span class="n">info</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here we are able to see the information of our dataframe, with the top 30 rows and the bottom 30 rows.</p>
<p>And, it also shows us the whole data frame has 205 rows and 26 columns in total.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="2.-Data-Wrangling">2. Data Wrangling<a class="anchor-link" href="#2.-Data-Wrangling">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>What is the purpose of Data Wrangling?</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Data Wrangling is the process of converting data from the initial format to a format that may be better for analysis.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><em>(As we can see, several question marks appeared in the dataframe; those are missing values which may hinder our further analysis).</em></p>
<h3 id="How-do-we-identify-all-those-missing-values-and-deal-with-them-and-how-to-work-with-missing-data?">How do we identify all those missing values and deal with them and how to work with missing data?<a class="anchor-link" href="#How-do-we-identify-all-those-missing-values-and-deal-with-them-and-how-to-work-with-missing-data?">&#182;</a></h3><p>Steps for working with missing data:</p>
<ol>
<li>identify missing data</li>
<li>deal with missing data</li>
<li>correct data format</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref1"></a></p>
<h2 id="2.1.1-Identify-and-handle-missing-values">2.1.1 Identify and handle missing values<a class="anchor-link" href="#2.1.1-Identify-and-handle-missing-values">&#182;</a></h2><p><a id="ref2"></a></p>
<h4 id="Convert-&quot;?&quot;-to-NaN">Convert "?" to NaN<a class="anchor-link" href="#Convert-&quot;?&quot;-to-NaN">&#182;</a></h4><p>In the car dataset, missing data comes with the question mark "?".
We replace "?" with NaN (Not a Number), which is Python's default missing value marker, for reasons of computational speed and convenience. Here we use the function: 
 <pre>.replace(A, B, inplace = True) </pre>
to replace A by B</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="c1"># replace &quot;?&quot; to NaN</span>
<span class="n">df</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="s2">&quot;?&quot;</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Evaluating-for-Missing-Data">Evaluating for Missing Data<a class="anchor-link" href="#Evaluating-for-Missing-Data">&#182;</a></h4><p>The missing values are converted to Python's default. We use Python's built-in functions to identify these missing values. There are two methods to detect missing data:</p>
<ol>
<li><strong>.isnull()</strong></li>
<li><strong>.notnull()</strong></li>
</ol>
<p>The output is a boolean value indicating whether the passed in argument value are in fact missing data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">missing_data</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span>
<span class="n">missing_data</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>"True" stands for missing value, while "False" stands for not missing value.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Count-missing-values-in-each-column">Count missing values in each column<a class="anchor-link" href="#Count-missing-values-in-each-column">&#182;</a></h4><p>Using a for loop in Python, we can quickly figure out the number of missing values in each column. As mentioned above, "True" represents a missing value, "False"  means the value is present in the dataset.  In the body of the for loop the method  ".value_couts()"  counts the number of "True" values.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">column</span> <span class="ow">in</span> <span class="n">missing_data</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">values</span><span class="o">.</span><span class="n">tolist</span><span class="p">():</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">column</span><span class="p">)</span>
    <span class="nb">print</span> <span class="p">(</span><span class="n">missing_data</span><span class="p">[</span><span class="n">column</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">())</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;&quot;</span><span class="p">)</span>    
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Based on the summary above, each column has 205 rows of data, seven columns containing missing data:</p>
<ol>
<li>"normalized-losses": 41 missing data</li>
<li>"num-of-doors": 2 missing data</li>
<li>"bore": 4 missing data</li>
<li>"stroke" : 4 missing data</li>
<li>"horsepower": 2 missing data</li>
<li>"peak-rpm": 2 missing data</li>
<li>"price": 4 missing data</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref3"></a></p>
<h2 id="2.1.2-Deal-with-missing-data">2.1.2 Deal with missing data<a class="anchor-link" href="#2.1.2-Deal-with-missing-data">&#182;</a></h2><p><strong>How to deal with missing data?</strong></p>

<pre><code>1. drop data 
    a. drop the whole row
    b. drop the whole column
2. replace data
    a. replace it by mean
    b. replace it by frequency
    c. replace it based on other functions</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Whole columns should be dropped only if most entries in the column are empty. In our dataset, none of the columns are empty enough to drop entirely.
We have some freedom in choosing which method to replace data; however, some methods may seem more reasonable than others. We will apply each method to many different columns:</p>
<p><strong>Replace by mean:</strong></p>

<pre><code>"normalized-losses": 41 missing data, replace them with mean
"stroke": 4 missing data, replace them with mean
"bore": 4 missing data, replace them with mean
"horsepower": 2 missing data, replace them with mean
"peak-rpm": 2 missing data, replace them with mean

</code></pre>
<p><strong>Replace by frequency:</strong></p>

<pre><code>"num-of-doors": 2 missing data, replace them with "four". 
    * Reason: 84% sedans is four doors. Since four doors is most frequent, it is most likely to 


</code></pre>
<p><strong>Drop the whole row:</strong></p>

<pre><code>"price": 4 missing data, simply delete the whole row
    * Reason: price is what we want to predict. Any data entry without price data cannot be used for prediction; therefore they are not useful to us</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Calculate-the-average-of-the-column">Calculate the average of the column<a class="anchor-link" href="#Calculate-the-average-of-the-column">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">avg_1</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s2">&quot;normalized-losses&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s2">&quot;float&quot;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">axis</span> <span class="o">=</span> <span class="mi">0</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Replace-&quot;NaN&quot;-by-mean-value-in-&quot;normalized-losses&quot;-column">Replace "NaN" by mean value in "normalized-losses" column<a class="anchor-link" href="#Replace-&quot;NaN&quot;-by-mean-value-in-&quot;normalized-losses&quot;-column">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;normalized-losses&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">avg_1</span><span class="p">,</span> <span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Calculate-the-mean-value-for-'bore'-column">Calculate the mean value for 'bore' column<a class="anchor-link" href="#Calculate-the-mean-value-for-'bore'-column">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">avg_2</span><span class="o">=</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;bore&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;float&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Replace-NaN-by-mean-value">Replace NaN by mean value<a class="anchor-link" href="#Replace-NaN-by-mean-value">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;bore&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">avg_2</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-4:-According-to-the-example-above,-replace-NaN-in-&quot;stroke&quot;-column-by-mean.">Question 4: According to the example above, replace NaN in "stroke" column by mean.<a class="anchor-link" href="#Question-4:-According-to-the-example-above,-replace-NaN-in-&quot;stroke&quot;-column-by-mean.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># calculate the mean vaule for &quot;stroke&quot; column</span>
<span class="n">avg_3</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s2">&quot;stroke&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;float&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>

<span class="c1"># replace NaN by mean value in &quot;stroke&quot; column</span>
<span class="n">df</span><span class="p">[</span><span class="s2">&quot;stroke&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">avg_3</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Calculate-the-mean-value-for-the--'horsepower'-column:">Calculate the mean value for the  'horsepower' column:<a class="anchor-link" href="#Calculate-the-mean-value-for-the--'horsepower'-column:">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">avg_4</span><span class="o">=</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;float&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Replace-&quot;NaN&quot;-by-mean-value-:">Replace "NaN" by mean value :<a class="anchor-link" href="#Replace-&quot;NaN&quot;-by-mean-value-:">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">avg_4</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Calculate-the-mean-value-for-'peak-rpm'-column:">Calculate the mean value for 'peak-rpm' column:<a class="anchor-link" href="#Calculate-the-mean-value-for-'peak-rpm'-column:">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">avg_5</span><span class="o">=</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;peak-rpm&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;float&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Replace-NaN-by-mean-value:">Replace NaN by mean value:<a class="anchor-link" href="#Replace-NaN-by-mean-value:">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;peak-rpm&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">avg_5</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To see which values are present in a particular column, we can use the ".value_counts()" method:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;num-of-doors&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can see that four doors are the most common type. We can also use the ".idxmax()" method to calculate for us the most common type automatically:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;num-of-doors&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">idxmax</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The replacement procedure is very similar to what we have seen previously</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#replace the missing &#39;num-of-doors&#39; values by the most frequent </span>
<span class="n">df</span><span class="p">[</span><span class="s2">&quot;num-of-doors&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="s2">&quot;four&quot;</span><span class="p">,</span> <span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Finally, let's drop all rows that do not have price data:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># simply drop whole row with NaN in &quot;price&quot; column</span>
<span class="n">df</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">subset</span><span class="o">=</span><span class="p">[</span><span class="s2">&quot;price&quot;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span> <span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>

<span class="c1"># reset index, because we droped two rows</span>
<span class="n">df</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span> <span class="o">=</span> <span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Good!</strong> Now, we obtain the dataset with no missing values.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref4"></a></p>
<h2 id="2.1.3-Correct--data-format">2.1.3 Correct  data format<a class="anchor-link" href="#2.1.3-Correct--data-format">&#182;</a></h2><p><strong>We are almost there!</strong></p>
<div>The last step in data cleaning is checking and making sure that all data is in the correct format (int, float, text or other).</div><p>In Pandas, we use</p>
<div>**.dtype()** to check the data type</div>
<div>**.astype()** to change the data type</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Lets-list-the-data-types-for-each-column">Lets list the data types for each column<a class="anchor-link" href="#Lets-list-the-data-types-for-each-column">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">dtypes</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As we can see above, some columns are not of the correct data type. Numerical variables should have type 'float' or 'int', and variables with strings such as categories should have type 'object'. For example, 'bore' and 'stroke' variables are numerical values that describe the engines, so we should expect them to be of the type 'float' or 'int'; however, they are shown as type 'object'. We have to convert data types into a proper format for each column using the "astype()" method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Convert-data-types-to-proper-format">Convert data types to proper format<a class="anchor-link" href="#Convert-data-types-to-proper-format">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s2">&quot;bore&quot;</span><span class="p">,</span> <span class="s2">&quot;stroke&quot;</span><span class="p">]]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s2">&quot;bore&quot;</span><span class="p">,</span> <span class="s2">&quot;stroke&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s2">&quot;float&quot;</span><span class="p">)</span>
<span class="n">df</span><span class="p">[[</span><span class="s2">&quot;normalized-losses&quot;</span><span class="p">]]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s2">&quot;normalized-losses&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s2">&quot;int&quot;</span><span class="p">)</span>
<span class="n">df</span><span class="p">[[</span><span class="s2">&quot;price&quot;</span><span class="p">]]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s2">&quot;price&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s2">&quot;float&quot;</span><span class="p">)</span>
<span class="n">df</span><span class="p">[[</span><span class="s2">&quot;peak-rpm&quot;</span><span class="p">]]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s2">&quot;peak-rpm&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s2">&quot;float&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Done&quot;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Let-us-list-the-columns-after-the-conversion">Let us list the columns after the conversion<a class="anchor-link" href="#Let-us-list-the-columns-after-the-conversion">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">dtypes</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Wonderful!</strong></p>
<p>Now, we finally obtain the cleaned dataset with no missing values and all data in its proper format.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref5"></a></p>
<h2 id="2.2-Data-Standardization">2.2 Data Standardization<a class="anchor-link" href="#2.2-Data-Standardization">&#182;</a></h2><p>Data is usually collected from different agencies with different formats.
(Data Standardization is also a term for a particular type of data normalization, where we subtract the mean and divide by the standard deviation)</p>
<p><strong>What is Standardization?</strong></p>
<div>Standardization is the process of transforming data into a common format which allows the researcher to make the meaningful comparison.
</div><p><strong>Example</strong></p>
<div>Transform mpg to L/100km:</div>
<div>In our dataset, the fuel consumption columns "city-mpg" and "highway-mpg" are represented by mpg (miles per gallon) unit. Assume we are developing an application in a country that accept the fuel consumption with L/100km standard</div>
<div>We will need to apply **data transformation** to transform mpg into L/100km?</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The formula for unit conversion is
L/100km = 235 / mpg</p>
<div>We can do many mathematical operations directly in Pandas.</div>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># transform mpg to L/100km by mathematical operation (235 divided by mpg)</span>
<span class="n">df</span><span class="p">[</span><span class="s1">&#39;city-L/100km&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="mi">235</span><span class="o">/</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;city-mpg&quot;</span><span class="p">]</span>

<span class="c1"># check your transformed data </span>
<span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-5:-According-to-the-example-above,-transform-mpg-to-L/100km-in-the-column-of-&quot;highway-mpg&quot;,-and-change-the-name-of-column-to-&quot;highway-L/100km&quot;.">Question 5: According to the example above, transform mpg to L/100km in the column of "highway-mpg", and change the name of column to "highway-L/100km".<a class="anchor-link" href="#Question-5:-According-to-the-example-above,-transform-mpg-to-L/100km-in-the-column-of-&quot;highway-mpg&quot;,-and-change-the-name-of-column-to-&quot;highway-L/100km&quot;.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># transform mpg to L/100km by mathematical operation (235 divided by mpg)</span>
<span class="n">df</span><span class="p">[</span><span class="s2">&quot;highway-mpg&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="mi">235</span><span class="o">/</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;highway-mpg&quot;</span><span class="p">]</span>

<span class="c1"># rename column name from &quot;highway-mpg&quot; to &quot;highway-L/100km&quot;</span>
<span class="n">df</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;&quot;highway-mpg&quot;&#39;</span><span class="p">:</span><span class="s1">&#39;highway-L/100km&#39;</span><span class="p">},</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># check your transformed data </span>
<span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref6"></a></p>
<h2 id="2.3-Data-Normalization">2.3 Data Normalization<a class="anchor-link" href="#2.3-Data-Normalization">&#182;</a></h2><p><strong>Why normalization?</strong></p>
<div>Normalization is the process of transforming values of several variables into a similar range. Typical normalizations include scaling the variable so the variable average is 0, scaling the variable so the variable variance is 1, or scaling variable so the variable values range from 0 to 1
 </div><p><strong>Example</strong></p>
<div>To demonstrate normalization, let's say we want to scale the columns "length", "width" and "height" </div>
<div>**Target:** we would like to Normalize those variables so their value ranges from 0 to 1.</div>
<div>**Approach:** replace origianl value by (original value)/(maximum value)</div>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># replace (origianl value) by (original value)/(maximum value)</span>
<span class="n">df</span><span class="p">[</span><span class="s1">&#39;length&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;length&#39;</span><span class="p">]</span><span class="o">/</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;length&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>
<span class="n">df</span><span class="p">[</span><span class="s1">&#39;width&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;width&#39;</span><span class="p">]</span><span class="o">/</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;width&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Questiont-6:-According-to-the-example-above,-normalize-the-column-&quot;height&quot;.">Questiont 6: According to the example above, normalize the column "height".<a class="anchor-link" href="#Questiont-6:-According-to-the-example-above,-normalize-the-column-&quot;height&quot;.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;height&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;height&#39;</span><span class="p">]</span><span class="o">/</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;height&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span> 

<span class="c1"># show the scaled columns</span>
<span class="n">df</span><span class="p">[[</span><span class="s2">&quot;length&quot;</span><span class="p">,</span><span class="s2">&quot;width&quot;</span><span class="p">,</span><span class="s2">&quot;height&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here we can see, we've normalized "length", "width" and "height" in the range of [0,1].</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.4-Binning">2.4 Binning<a class="anchor-link" href="#2.4-Binning">&#182;</a></h2><p><strong>Why binning?</strong></p>
<div>Binning is a process of transforming continuous numerical variables into discrete categorical 'bins', for grouped analysis.
 </div><p><strong>Example: </strong></p>
<div>In our dataset, "horsepower" is a real valued variable ranging from 48 to 288, it has 57 unique values. What if we only care about the price difference between cars with high horsepower, medium horsepower, and little horsepower (3 types)? Can we rearrange them into three ‘bins' to simplify analysis? </div><div>We will use the Pandas method 'cut' to segment the 'horsepower' column into 3 bins </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Example-of-Binning-Data-In-Pandas">Example of Binning Data In Pandas<a class="anchor-link" href="#Example-of-Binning-Data-In-Pandas">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Convert data to correct format</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">]</span><span class="o">=</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">float</span><span class="p">,</span> <span class="n">copy</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We would like four bins of equal size bandwidth,the forth is because the function "cut"  include the rightmost edge:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">binwidth</span> <span class="o">=</span> <span class="p">(</span><span class="nb">max</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">])</span><span class="o">-</span><span class="nb">min</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">]))</span><span class="o">/</span><span class="mi">4</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We build a bin array, with a minimum value to a maximum value, with bandwidth calculated above. The bins will be values used to determine when one bin ends and another begins.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">bins</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="nb">min</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">]),</span> <span class="nb">max</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">]),</span> <span class="n">binwidth</span><span class="p">)</span>
<span class="n">bins</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We set group  names:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">group_names</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Low&#39;</span><span class="p">,</span> <span class="s1">&#39;Medium&#39;</span><span class="p">,</span> <span class="s1">&#39;High&#39;</span><span class="p">]</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We apply the function "cut" the determine what each value of "df['horsepower']" belongs to.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;horsepower-binned&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">cut</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">],</span> <span class="n">bins</span><span class="p">,</span> <span class="n">labels</span><span class="o">=</span><span class="n">group_names</span><span class="p">,</span><span class="n">include_lowest</span><span class="o">=</span><span class="kc">True</span> <span class="p">)</span>
<span class="n">df</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span><span class="s1">&#39;horsepower-binned&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">20</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Check the dataframe above carefully, you will find the last column provides the bins for "horsepower" with 3 categories ("Low","Medium" and "High").</p>
<div>We successfully narrow the intervals from 57 to 3!</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Bins-visualization">Bins visualization<a class="anchor-link" href="#Bins-visualization">&#182;</a></h3><p>Normally, a histogram is used to visualize the distribution of bins we created above.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="o">%</span><span class="k">matplotlib</span> inline
<span class="kn">import</span> <span class="nn">matplotlib</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">from</span> <span class="nn">matplotlib</span> <span class="k">import</span> <span class="n">pyplot</span>

<span class="n">a</span> <span class="o">=</span> <span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">)</span>

<span class="c1"># draw historgram of attribute &quot;horsepower&quot; with bins = 3</span>
<span class="n">plt</span><span class="o">.</span><span class="n">pyplot</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">],</span> <span class="n">bins</span> <span class="o">=</span> <span class="mi">3</span><span class="p">)</span>

<span class="c1"># set x/y labels and plot title</span>
<span class="n">plt</span><span class="o">.</span><span class="n">pyplot</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s2">&quot;horsepower&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">pyplot</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s2">&quot;count&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">pyplot</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s2">&quot;horsepower bins&quot;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The plot above shows the binning result for attribute "horsepower".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.5-Indicator-variable-(or-dummy-variable)">2.5 Indicator variable (or dummy variable)<a class="anchor-link" href="#2.5-Indicator-variable-(or-dummy-variable)">&#182;</a></h2><p><strong>What is an indicator variable?</strong></p>
<div>An indicator variable (or dummy variable) is a numerical variable used to label categories. They are called 'dummies' because the numbers themselves don't have inherent meaning. </div><p><strong>Why we use indicator variables?</strong></p>
<div>So we can use categorical variables for regression analysis in the later modules.</div><p><strong>Example</strong></p>
<div>We see the column "fuel-type" has two unique values, "gas" or "diesel". Regression doesn't understand words, only numbers. To use this attribute in regression analysis, we convert "fuel-type" into indicator variables.</div><div>We will use the panda's method 'get_dummies' to assign numerical values to different categories of fuel type. </div>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">columns</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>get indicator variables and assign it to data frame "dummy_variable_1"</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">dummy_variable_1</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">get_dummies</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;fuel-type&quot;</span><span class="p">])</span>
<span class="n">dummy_variable_1</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>change column names for clarity</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">dummy_variable_1</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;fuel-type-diesel&#39;</span><span class="p">:</span><span class="s1">&#39;gas&#39;</span><span class="p">,</span> <span class="s1">&#39;fuel-type-diesel&#39;</span><span class="p">:</span><span class="s1">&#39;diesel&#39;</span><span class="p">},</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">dummy_variable_1</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We now have the value 0 to represent "gas" and 1 to represent "diesel" in the column "fuel-type". We will now insert this column back into our original dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># merge data frame &quot;df&quot; and &quot;dummy_variable_1&quot; </span>
<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">df</span><span class="p">,</span> <span class="n">dummy_variable_1</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="c1"># drop original column &quot;fuel-type&quot; from &quot;df&quot;</span>
<span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="s2">&quot;fuel-type&quot;</span><span class="p">,</span> <span class="n">axis</span> <span class="o">=</span> <span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The last two columns are now the indicator variable representation of the fuel-type variable. It's all 0s and 1s now.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-7:-As-above,-create-indicator-variable-to-the-column-of-&quot;aspiration&quot;:-&quot;std&quot;-to-0,-while-&quot;turbo&quot;-to-1.">Question 7: As above, create indicator variable to the column of "aspiration": "std" to 0, while "turbo" to 1.<a class="anchor-link" href="#Question-7:-As-above,-create-indicator-variable-to-the-column-of-&quot;aspiration&quot;:-&quot;std&quot;-to-0,-while-&quot;turbo&quot;-to-1.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># get indicator variables of aspiration and assign it to data frame &quot;dummy_variable_2&quot;</span>
<span class="n">dummy_variable_2</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">get_dummies</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;aspiration&#39;</span><span class="p">])</span>

<span class="c1"># change column names for clarity</span>
<span class="n">dummy_variable_2</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;std&#39;</span><span class="p">:</span><span class="s1">&#39;aspiration-std&#39;</span><span class="p">,</span> <span class="s1">&#39;turbo&#39;</span><span class="p">:</span> <span class="s1">&#39;aspiration-turbo&#39;</span><span class="p">},</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># show first 5 instances of data frame &quot;dummy_variable_1&quot;</span>
<span class="n">dummy_variable_2</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-8:-Merge-the-new-dataframe-to-the-original-dataframe-then-drop-the-column-'aspiration'&lt;/b&gt;">Question 8: Merge the new dataframe to the original dataframe then drop the column 'aspiration'&lt;/b&gt;<a class="anchor-link" href="#Question-8:-Merge-the-new-dataframe-to-the-original-dataframe-then-drop-the-column-'aspiration'&lt;/b&gt;">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#merge the new dataframe to the original datafram</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">df</span><span class="p">,</span> <span class="n">dummy_variable_2</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="c1"># drop original column &quot;aspiration&quot; from &quot;df&quot;</span>
<span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="s1">&#39;aspiration&#39;</span><span class="p">,</span> <span class="n">axis</span> <span class="o">=</span> <span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>save the new csv</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;clean_df.csv&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.-Exploratory-Data-Analysis">3. Exploratory Data Analysis<a class="anchor-link" href="#3.-Exploratory-Data-Analysis">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: What are the main characteristics which have the most impact on the car price?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.1-Analyzing-Individual-Feature-Patterns-using-Visualization">3.1 Analyzing Individual Feature Patterns using Visualization<a class="anchor-link" href="#3.1-Analyzing-Individual-Feature-Patterns-using-Visualization">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Import visualization packages "Matplotlib" and "Seaborn", don't forget about "%matplotlib inline" to plot in a Jupyter notebook.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="o">%</span><span class="k">matplotlib</span> inline 
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="How-to-choose-the-right-visualization-method-?">How to choose the right visualization method ?<a class="anchor-link" href="#How-to-choose-the-right-visualization-method-?">&#182;</a></h3><p>When visualizing individual variables, it is important to first understand what type of variable you are dealing with. This will help us find the right visualisation method for that variable.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># list the data types for each column</span>
<span class="n">df</span><span class="o">.</span><span class="n">dtypes</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-9:-What-is-the-data-type-of-the-colunm-&quot;peak-rpm&quot;?">Question 9: What is the data type of the colunm "peak-rpm"?<a class="anchor-link" href="#Question-9:-What-is-the-data-type-of-the-colunm-&quot;peak-rpm&quot;?">&#182;</a></h3>
</div>
</div>
</div>float64
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>for example, we can calculate the correlation between variables  of type "int64" or "float64" using the method "corr":</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The diagonal elements are always one; we will study correlation more precisely Pearson correlation in-depth at the end of the notebook.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-10:-Find-the-correlation-between-the-following-columns-(bore,-stroke,compression-ratio,-and-horsepower)?">Question 10: Find the correlation between the following columns (bore, stroke,compression-ratio, and horsepower)?<a class="anchor-link" href="#Question-10:-Find-the-correlation-between-the-following-columns-(bore,-stroke,compression-ratio,-and-horsepower)?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;bore&#39;</span><span class="p">,</span> <span class="s1">&#39;stroke&#39;</span><span class="p">,</span> <span class="s1">&#39;compression-ratio&#39;</span><span class="p">,</span> <span class="s1">&#39;horsepower&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Continuous-numerical-variables:">Continuous numerical variables:<a class="anchor-link" href="#Continuous-numerical-variables:">&#182;</a></h3><p>Continuous numerical variables are variables that may contain any value within some range. Continuous numerical variables can have the type "int64" or "float64". A great way to visualize these variables is by using scatterplots with fitted lines.</p>
<p>In order to start understanding the (linear) relationship between an individual variable and the price. We can do this by using "regplot", which plots the scatterplot plus the fitted regression line for the data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's see several examples of different linear relationships:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Positive-linear-relationship">Positive linear relationship<a class="anchor-link" href="#Positive-linear-relationship">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's find the scatterplot of "engine-size" and "price"</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Engine size as potential predictor variable of price</span>
<span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;engine-size&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylim</span><span class="p">(</span><span class="mi">0</span><span class="p">,)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As the engine-size goes up, the price goes up: this indicates a positive direct correlation between these two variables. Engine size seems like a pretty good predictor of price since the regression line is almost a perfect diagonal line. E</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can examine the correlation between 'engine-size' and 'price' and see it's approximately  0.87</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s2">&quot;engine-size&quot;</span><span class="p">,</span> <span class="s2">&quot;price&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Negative-linear-relationship">Negative linear relationship<a class="anchor-link" href="#Negative-linear-relationship">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Highway mpg is a potential predictor variable of price</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;highway-mpg&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As the highway-mpg goes up, the price goes down: this indicates an inverse/ negative relationship between these two variables. Highway mpg could potentially be a predictor of price.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can examine the correlation between 'highway-mpg' and 'price' and see it's approximately  -0.704</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;highway-mpg&#39;</span><span class="p">,</span> <span class="s1">&#39;price&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Weak-Linear-Relationship">Weak Linear Relationship<a class="anchor-link" href="#Weak-Linear-Relationship">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's see if "Peak-rpm" as a predictor variable of "price".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;peak-rpm&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Peak rpm does not seem like a good predictor of the price at all since the regression line is close to horizontal. Also, the data points are very scattered and far from the fitted line, showing lots of variability. Therefore it's it is not a reliable variable.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we can examine the correlation between 'peak-rpm'  and 'price'and see it's approximately  -0.101616</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;peak-rpm&#39;</span><span class="p">,</span><span class="s1">&#39;price&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-11(a):-Find-the-correlation--between-x=&quot;stroke&quot;,-y=&quot;price&quot;.">Question 11(a): Find the correlation  between x="stroke", y="price".<a class="anchor-link" href="#Question-11(a):-Find-the-correlation--between-x=&quot;stroke&quot;,-y=&quot;price&quot;.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># The correlation is 0.0823, the non-diagonal elements of the table.</span>
<span class="n">code</span><span class="p">:</span><span class="n">df</span><span class="p">[[</span><span class="s2">&quot;stroke&quot;</span><span class="p">,</span><span class="s2">&quot;price&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-11(b):-Given-the-correlation-results-between-&quot;price&quot;-and-&quot;stroke&quot;--do-you-expect-a-linear-relationship?-Verify-your-results-using-the-function-&quot;regplot()&quot;.">Question 11(b): Given the correlation results between "price" and "stroke"  do you expect a linear relationship? Verify your results using the function "regplot()".<a class="anchor-link" href="#Question-11(b):-Given-the-correlation-results-between-&quot;price&quot;-and-&quot;stroke&quot;--do-you-expect-a-linear-relationship?-Verify-your-results-using-the-function-&quot;regplot()&quot;.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># There is a weak correlation between the variable &#39;stroke&#39; and &#39;price.&#39; as such regression will not work well.We can see this use &quot;regplot&quot; to demonstrate this.</span>
<span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;stroke&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.2-Categorical-variables">3.2 Categorical variables<a class="anchor-link" href="#3.2-Categorical-variables">&#182;</a></h2><p>These are variables that describe a 'characteristic' of a data unit, and are selected from a small group of categories. The categorical variables can have the type "object" or "int64". A good way to visualize categorical variables is by using boxplots.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's look at the relationship between "body-style" and "price".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;body-style&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We see that the distributions of price between the different body-style categories have a significant overlap, and so body-style would not be a good predictor of price. Let's examine engine "engine-location" and "price" :</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;engine-location&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here we see that the distribution of price between these two engine-location categories, front and rear, are distinct enough to take engine-location as a potential good predictor of price.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's examine "drive-wheels" and "price".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># drive-wheels</span>
<span class="n">sns</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;drive-wheels&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here we see that the distribution of price between the different drive-wheels categories differs; as such drive-wheels could potentially be a predictor of price.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.3-Descriptive-Statistical-Analysis">3.3 Descriptive Statistical Analysis<a class="anchor-link" href="#3.3-Descriptive-Statistical-Analysis">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's first take a look at the variables by utilising a description method.</p>
<p>The <strong>describe</strong> function automatically computes basic statistics for all continuous variables. Any NaN values are automatically skipped in these statistics.</p>
<p>This will show:</p>
<ul>
<li>the count of that variable</li>
<li>the mean</li>
<li>the standard deviation (std) </li>
<li>the minimum value</li>
<li>the IQR (Interquartile Range: 25%, 50% and 75%)</li>
<li>the maximum value</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can apply the method "describe" as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The default setting of "describe" skips variables of type object. We can apply the method "describe" on the variables of type 'object' as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">(</span><span class="n">include</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;object&#39;</span><span class="p">])</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Value-Counts">Value Counts<a class="anchor-link" href="#Value-Counts">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Value-counts is a good way of understanding how many units of each characteristic/variable we have. We can apply the "value_counts" method on the column   'drive-wheels'. Don’t forget the method "value_counts" only works on Pandas series, not Pandas Dataframes. As a result, we only include one bracket  "df['drive-wheels']" not two brackets "df[['drive-wheels']]".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can convert the series to a Dataframe as follows :</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">to_frame</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's repeat the above steps but save the results to the dataframe "drive_wheels_counts" and rename the column  'drive-wheels' to 'value_counts'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">drive_wheels_counts</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">to_frame</span><span class="p">()</span>
<span class="n">drive_wheels_counts</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">:</span> <span class="s1">&#39;value_counts&#39;</span><span class="p">},</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">drive_wheels_counts</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now let's rename the index to 'drive-wheels':</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">drive_wheels_counts</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="s1">&#39;drive-wheels&#39;</span>
<span class="n">drive_wheels_counts</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can repeat the above process for the variable 'engine-location'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># engine-location as variable</span>
<span class="n">engine_loc_counts</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;engine-location&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">to_frame</span><span class="p">()</span>
<span class="n">engine_loc_counts</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;engine-location&#39;</span><span class="p">:</span> <span class="s1">&#39;value_counts&#39;</span><span class="p">},</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">engine_loc_counts</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="s1">&#39;engine-location&#39;</span>
<span class="n">engine_loc_counts</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">10</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Examining the value counts of the engine location would not be a good predictor variable for the price. This is because we only have three cars with a rear engine and 198 with an engine in the front, this result is skewed. Thus, we are not able to draw any conclusions about the engine location.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.4-Basic-of-Grouping">3.4 Basic of Grouping<a class="anchor-link" href="#3.4-Basic-of-Grouping">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The "groupby" method groups data by different categories. The data is grouped based on one or several variables and analysis is performed on the individual groups.</p>
<p>For example, let's group by the variable "drive-wheels". We see that there are 3 different categories of drive wheels.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">unique</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>If we want to know, on average, which type of drive wheel is most valuable, we can group "drive-wheels" and then average them.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we can select the columns 'drive-wheels','body-style' and 'price' , then assign it to the variable "df_group_one".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_group_one</span><span class="o">=</span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">,</span><span class="s1">&#39;body-style&#39;</span><span class="p">,</span><span class="s1">&#39;price&#39;</span><span class="p">]]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we can then calculate the average price for each of the different categories of data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># grouping results</span>

<span class="n">df_group_one</span><span class="o">=</span><span class="n">df_group_one</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">],</span><span class="n">as_index</span><span class="o">=</span> <span class="kc">False</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">df_group_one</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>From our data, it seems rear-wheel drive vehicles are, on average, the most expensive, while 4-wheel and front-wheel are approximately the same in price.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>You can also group with multiple variables. For example, let's group by both 'drive-wheels' and 'body-style'. This groups the dataframe by the unique combinations 'drive-wheels' and 'body-style'. We can store the results in the variable 'grouped_test1'</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># grouping results</span>
<span class="n">df_gptest</span><span class="o">=</span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">,</span><span class="s1">&#39;body-style&#39;</span><span class="p">,</span><span class="s1">&#39;price&#39;</span><span class="p">]]</span>
<span class="n">grouped_test1</span><span class="o">=</span><span class="n">df_gptest</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">,</span><span class="s1">&#39;body-style&#39;</span><span class="p">],</span><span class="n">as_index</span><span class="o">=</span> <span class="kc">False</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">grouped_test1</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This grouped data is much easier to visualize when it is made into a pivot table. A pivot table is like an Excel spreadsheet, with one variable along the column and another along the row. We can convert the dataframe to a pivot table using the method "pivot " to create a pivot table from the groups.</p>
<p>In this case, we will leave the drive-wheel variable as the rows of the table, and pivot body-style to become the columns of the table:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">grouped_pivot</span><span class="o">=</span><span class="n">grouped_test1</span><span class="o">.</span><span class="n">pivot</span><span class="p">(</span><span class="n">index</span><span class="o">=</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">,</span><span class="n">columns</span><span class="o">=</span><span class="s1">&#39;body-style&#39;</span><span class="p">)</span>
<span class="n">grouped_pivot</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Often, we won't have data for some of the pivot cells. We can fill these missing cells with the value 0, but any other value could potentially be used as well. It should be mentioned that missing data is quite a complex subject and is an entire course on its own.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">grouped_pivot</span><span class="o">=</span><span class="n">grouped_pivot</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span> <span class="c1">#fill missing values with 0</span>
<span class="n">grouped_pivot</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-12-:Use-the-&quot;groupby&quot;-function-to-find-the-average-&quot;price&quot;-of-each-car-based-on-&quot;body-style&quot;-?">Question 12 :Use the "groupby" function to find the average "price" of each car based on "body-style" ?<a class="anchor-link" href="#Question-12-:Use-the-&quot;groupby&quot;-function-to-find-the-average-&quot;price&quot;-of-each-car-based-on-&quot;body-style&quot;-?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_group_two</span><span class="o">=</span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;body-style&#39;</span><span class="p">,</span><span class="s1">&#39;price&#39;</span><span class="p">]]</span>
<span class="n">df_group_two</span><span class="o">=</span><span class="n">df_group_two</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;body-style&#39;</span><span class="p">],</span><span class="n">as_index</span><span class="o">=</span> <span class="kc">False</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">df_group_two</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>If you didn't import "pyplot" let's do it again.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="o">%</span><span class="k">matplotlib</span> inline 
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Variables:-Drive-Wheels-and-Body-Style-vs-Price">Variables: Drive Wheels and Body Style vs Price<a class="anchor-link" href="#Variables:-Drive-Wheels-and-Body-Style-vs-Price">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's use a heat map to visualize the relationship between Body Style vs Price</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#use the grouped results</span>
<span class="n">plt</span><span class="o">.</span><span class="n">pcolor</span><span class="p">(</span><span class="n">grouped_pivot</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="s1">&#39;RdBu&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">colorbar</span><span class="p">()</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The heatmap plots the target variable (price) proportional to colour with respect to the variables 'drive-wheel' and 'body-style' in the vertical and horizontal axis respectively. This allows us to visualize how the price is related to 'drive-wheel' and 'body-style', 
The default labels convey no useful information to us. Let's change that:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">()</span>
<span class="n">im</span><span class="o">=</span><span class="n">ax</span><span class="o">.</span><span class="n">pcolor</span><span class="p">(</span><span class="n">grouped_pivot</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="s1">&#39;RdBu&#39;</span><span class="p">)</span>

<span class="c1">#label names</span>
<span class="n">row_labels</span><span class="o">=</span><span class="n">grouped_pivot</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">levels</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span>
<span class="n">col_labels</span><span class="o">=</span><span class="n">grouped_pivot</span><span class="o">.</span><span class="n">index</span>
<span class="c1">#move ticks and labels to the center</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_xticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="n">grouped_pivot</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">1</span><span class="p">])</span><span class="o">+</span><span class="mf">0.5</span><span class="p">,</span> <span class="n">minor</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_yticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="n">grouped_pivot</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">])</span><span class="o">+</span><span class="mf">0.5</span><span class="p">,</span> <span class="n">minor</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="c1">#insert labels</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_xticklabels</span><span class="p">(</span><span class="n">row_labels</span><span class="p">,</span> <span class="n">minor</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_yticklabels</span><span class="p">(</span><span class="n">col_labels</span><span class="p">,</span> <span class="n">minor</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="c1">#rotate label if too long</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="n">rotation</span><span class="o">=</span><span class="mi">90</span><span class="p">)</span>

<span class="n">fig</span><span class="o">.</span><span class="n">colorbar</span><span class="p">(</span><span class="n">im</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Visualization is very important in data science, and Python visualization packages provide great freedom. We will go more in-depth in a separate Python Visualizations course.</p>
<p>The main question we want to answer in this module, is "What are the main characteristics which have the most impact on the car price?".</p>
<p>To get a better measure of the important characteristics, we look at the correlation of these variables with the car price, in other words: how is the car price dependent on this variable?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.5-Correlation-and-Causation">3.5 Correlation and Causation<a class="anchor-link" href="#3.5-Correlation-and-Causation">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Correlation</strong>: a measure of the extent of interdependence between variables.</p>
<p><strong>Causation</strong>: the relationship between cause and effect between two variables.</p>
<p>It is important to know the difference between these two and that correlation does not imply causation. Determining  correlation is much simpler  the determining causation as causation may require independent experimentation</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Pearson-Correlation">Pearson Correlation<a class="anchor-link" href="#Pearson-Correlation">&#182;</a></h3><p>The Pearson Correlation measures the linear dependence between two variables X and Y.
The resulting coefficient is a value between -1 and 1 inclusive, where:</p>
<ul>
<li><strong>1</strong>: total positive linear correlation,</li>
<li><strong>0</strong>: no linear correlation, the two variables most likely do not affect each other</li>
<li><strong>-1</strong>: total negative linear correlation.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Pearson Correlation is the default method of the function "corr".  Like before we can calculate the Pearson correlation of the of the 'int64' or 'float64'  variables.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>sometimes we would like to know the significant of the correlation estimate.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>P-value</strong>: 
What is this P-value? The P-value is the probability value that the correlation between these two variables is statistically significant. Normally, we choose a significance level of 0.05, which means that we are 95% confident that the correlation between the variables is significant.</p>
<p>By convention, when the</p>
<ul>
<li>p-value is &lt; 0.001 we say there is strong evidence that the correlation is significant,</li>
<li>the p-value is &lt; 0.05; there is moderate evidence that the correlation is significant,</li>
<li>the p-value is &lt; 0.1; there is weak evidence that the correlation is significant, and</li>
<li>the p-value is &gt; 0.1; there is no evidence that the correlation is significant.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can obtain this information using  "stats" module in the "scipy"  library.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">scipy</span> <span class="k">import</span> <span class="n">stats</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Wheel-base-vs-Price">Wheel-base vs Price<a class="anchor-link" href="#Wheel-base-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the  Pearson Correlation Coefficient and P-value of 'wheel-base' and 'price'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;wheel-base&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span><span class="p">)</span>  
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between wheel-base and price is statistically significant, although the linear relationship isn't extremely strong (~0.585)</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Horsepower-vs-Price">Horsepower vs Price<a class="anchor-link" href="#Horsepower-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the  Pearson Correlation Coefficient and P-value of 'horsepower' and 'price'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span><span class="p">)</span>  
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between horsepower and price is statistically significant, and the linear relationship is quite strong (~0.809, close to 1)</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Length-vs-Price">Length vs Price<a class="anchor-link" href="#Length-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the  Pearson Correlation Coefficient and P-value of 'length' and 'price'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;length&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span><span class="p">)</span>  
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between length and price is statistically significant, and the linear relationship is moderately strong (~0.691).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Width-vs-Price">Width vs Price<a class="anchor-link" href="#Width-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the Pearson Correlation Coefficient and P-value of 'width' and 'price':</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;width&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span> <span class="p">)</span> 
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between width and price is statistically significant, and the linear relationship is quite strong (~0.751).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Curb-weight-vs-Price">Curb-weight vs Price<a class="anchor-link" href="#Curb-weight-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the Pearson Correlation Coefficient and P-value of 'curb-weight' and 'price':</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;curb-weight&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span> <span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span><span class="p">)</span>  
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between curb-weight and price is statistically significant, and the linear relationship is quite strong (~0.834).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Engine-size-vs-Price">Engine-size vs Price<a class="anchor-link" href="#Engine-size-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the Pearson Correlation Coefficient and P-value of 'engine-size' and 'price':</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;engine-size&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span><span class="p">)</span> 
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between engine-size and price is statistically significant, and the linear relationship is very strong (~0.872).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Bore-vs-Price">Bore vs Price<a class="anchor-link" href="#Bore-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the  Pearson Correlation Coefficient and P-value of 'bore' and 'price':</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;bore&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span> <span class="p">)</span> 
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between bore and price is statistically significant, but the linear relationship is only moderate (~0.521).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can relate the process for each 'City-mpg'  and 'Highway-mpg':</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="City-mpg-vs-Price">City-mpg vs Price<a class="anchor-link" href="#City-mpg-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;city-mpg&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span><span class="p">)</span>  
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between city-mpg and price is statistically significant, and the coefficient of ~ -0.687 shows that the relationship is negative and moderately strong.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Highway-mpg-vs-Price">Highway-mpg vs Price<a class="anchor-link" href="#Highway-mpg-vs-Price">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pearson_coef</span><span class="p">,</span> <span class="n">p_value</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">pearsonr</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;highway-mpg&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span> <span class="s2">&quot;The Pearson Correlation Coefficient is&quot;</span><span class="p">,</span> <span class="n">pearson_coef</span><span class="p">,</span> <span class="s2">&quot; with a P-value of P =&quot;</span><span class="p">,</span> <span class="n">p_value</span> <span class="p">)</span> 
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Conclusion:">Conclusion:<a class="anchor-link" href="#Conclusion:">&#182;</a></h5><p>Since the p-value is &lt; 0.001, the correlation between highway-mpg and price is statistically significant, and the coefficient of ~ -0.705 shows that the relationship is negative and moderately strong.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.6-ANOVA">3.6 ANOVA<a class="anchor-link" href="#3.6-ANOVA">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="ANOVA:-Analysis-of-Variance">ANOVA: Analysis of Variance<a class="anchor-link" href="#ANOVA:-Analysis-of-Variance">&#182;</a></h3><p>The Analysis of Variance  (ANOVA) is a statistical method used to test whether there are significant differences between the means of two or more groups. ANOVA returns two parameters:</p>
<p><strong>F-test score</strong>: ANOVA assumes the means of all groups are the same, calculates how much the actual means deviate from the assumption, and reports it as the F-test score. A larger score means there is a larger difference between the means.</p>
<p><strong>P-value</strong>:  P-value tells how statistically significant is our calculated score value</p>
<p>If our price variable is strongly correlated with the variable we are analyzing, expect ANOVA to return a sizeable F-test score and a small p-value.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Drive-Wheels">Drive Wheels<a class="anchor-link" href="#Drive-Wheels">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Since ANOVA analyzes the difference between different groups of the same variable, the groupby function will come in handy. Because the ANOVA algorithm averages the data automatically, we do not need to take the average before hand.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's see if different types 'drive-wheels' impact  'price', we group the data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">grouped_test2</span><span class="o">=</span><span class="n">df_gptest</span><span class="p">[[</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">,</span><span class="s1">&#39;price&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;drive-wheels&#39;</span><span class="p">])</span>
<span class="n">grouped_test2</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can obtain the values of the method group using the method "get_group".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;4wd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">]</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we can use the function 'f_oneway' in the module 'stats'  to obtain the <strong>F-test score</strong> and <strong>P-value</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># ANOVA</span>
<span class="n">f_val</span><span class="p">,</span> <span class="n">p_val</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">f_oneway</span><span class="p">(</span><span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;fwd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;rwd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;4wd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>  
 
<span class="nb">print</span><span class="p">(</span> <span class="s2">&quot;ANOVA results: F=&quot;</span><span class="p">,</span> <span class="n">f_val</span><span class="p">,</span> <span class="s2">&quot;, P =&quot;</span><span class="p">,</span> <span class="n">p_val</span><span class="p">)</span>   
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This is a great result, with a large F test score showing a strong correlation and a P value of almost 0 implying almost certain statistical significance. But does this mean all three tested groups are all this highly correlated?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Separately:-fwd-and-rwd">Separately: fwd and rwd<a class="anchor-link" href="#Separately:-fwd-and-rwd">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">f_val</span><span class="p">,</span> <span class="n">p_val</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">f_oneway</span><span class="p">(</span><span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;fwd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;rwd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>  
 
<span class="nb">print</span><span class="p">(</span> <span class="s2">&quot;ANOVA results: F=&quot;</span><span class="p">,</span> <span class="n">f_val</span><span class="p">,</span> <span class="s2">&quot;, P =&quot;</span><span class="p">,</span> <span class="n">p_val</span> <span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's examine the other groups</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="4wd-and-rwd">4wd and rwd<a class="anchor-link" href="#4wd-and-rwd">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">f_val</span><span class="p">,</span> <span class="n">p_val</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">f_oneway</span><span class="p">(</span><span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;4wd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;rwd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>  
   
<span class="nb">print</span><span class="p">(</span> <span class="s2">&quot;ANOVA results: F=&quot;</span><span class="p">,</span> <span class="n">f_val</span><span class="p">,</span> <span class="s2">&quot;, P =&quot;</span><span class="p">,</span> <span class="n">p_val</span><span class="p">)</span>   
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="4wd-and-fwd">4wd and fwd<a class="anchor-link" href="#4wd-and-fwd">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">f_val</span><span class="p">,</span> <span class="n">p_val</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">f_oneway</span><span class="p">(</span><span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;4wd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">grouped_test2</span><span class="o">.</span><span class="n">get_group</span><span class="p">(</span><span class="s1">&#39;fwd&#39;</span><span class="p">)[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>  
 
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;ANOVA results: F=&quot;</span><span class="p">,</span> <span class="n">f_val</span><span class="p">,</span> <span class="s2">&quot;, P =&quot;</span><span class="p">,</span> <span class="n">p_val</span><span class="p">)</span>   
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Important-Variables">Important Variables<a class="anchor-link" href="#Important-Variables">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We now have a better idea of what our data looks like and which variables are important to take into account when predicting the car price. We have narrowed it down to the following variables:</p>
<p>Continuous numerical variables:</p>
<ul>
<li>Length</li>
<li>Width</li>
<li>Curb-weight</li>
<li>Engine-size</li>
<li>Horsepower</li>
<li>City-mpg</li>
<li>Highway-mpg</li>
<li>Wheel-base</li>
<li>Bore</li>
</ul>
<p>Categorical variables:</p>
<ul>
<li>Drive-wheels</li>
</ul>
<p>AS we now move into building machine learning models to automate our analysis, feeding the model with variables that meaningfully affect our target variable will improve our model's prediction performance.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="4.-Model-Development">4. Model Development<a class="anchor-link" href="#4.-Model-Development">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In this section, we will develop several models that will predict the price of the car using the variables or features. This is just an estimate but should give us an objective idea of how much the car should cost.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><h3>Questions:</h3> <h4>How do I know if the dealer is offering fair value for my trade-in and how do I know if I put a fair value on my car?</h4></p>
<p>In Data Analytics, we often use <strong>Model Development</strong> to help us predict future observations from the data we have.</p>
<p>A Model will help us understand the exact relationship between different variables and how these variables are used to predict the result.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.1-Linear-Regression-and-Multiple-Linear-Regression">4.1 Linear Regression and Multiple Linear Regression<a class="anchor-link" href="#4.1-Linear-Regression-and-Multiple-Linear-Regression">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.1.1-Linear-Regression">4.1.1 Linear Regression<a class="anchor-link" href="#4.1.1-Linear-Regression">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>One example of a Data  Model that we will be using is 
 <strong>Simple Linear Regression</strong>.
Simple Linear Regression is a method to help us understand the relationship between two variables:</p>
<ul>
<li>The predictor/independent variable (X)</li>
<li>The response/dependent variable (that we want to predict)(Y)</li>
</ul>
<p>The result of Linear Regression is a <strong>linear function</strong> that predicts the response (dependent) variable as a function of the predictor (independent) variable.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
\begin{equation*}
 Y: Response \ Variable\\
 X :Predictor\ Variables
\end{equation*}
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Linear-function:">Linear function:<a class="anchor-link" href="#Linear-function:">&#182;</a></h3>\begin{equation*}
Yhat = a + b  X
\end{equation*}
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li>a refers to the <strong>intercept</strong> of the regression, in other words: the value of Y when X is 0 </li>
<li>b refers to the <strong>slope</strong> of the regression line, in other words: the value with which Y changes when X increases by 1.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Lets-load-the-modules-for-linear-regression">Lets load the modules for linear regression<a class="anchor-link" href="#Lets-load-the-modules-for-linear-regression">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">LinearRegression</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Create-the-linear-regression-object">Create the linear regression object<a class="anchor-link" href="#Create-the-linear-regression-object">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm</span> <span class="o">=</span> <span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">lm</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="How-could-Highway-mpg-help-us-predict-car-price?">How could Highway-mpg help us predict car price?<a class="anchor-link" href="#How-could-Highway-mpg-help-us-predict-car-price?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For this example, we want to look at how highway-mpg can help us predict car price.
Using simple linear regression, we will create a linear function with "highway-mpg" as the predictor variable and the "price" as the response variable.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">X</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s1">&#39;highway-mpg&#39;</span><span class="p">]]</span>
<span class="n">Y</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">]</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Fit the linear model using highway-mpg.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span><span class="n">Y</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can output a prediction</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Yhat</span><span class="o">=</span><span class="n">lm</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">)</span>
<span class="n">Yhat</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">5</span><span class="p">]</span>   
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="What-is-the-value-of-the-intercept-(a)-?">What is the value of the intercept (a) ?<a class="anchor-link" href="#What-is-the-value-of-the-intercept-(a)-?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm</span><span class="o">.</span><span class="n">intercept_</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="What-is-the-value-of-the-Slope-(b)-?">What is the value of the Slope (b) ?<a class="anchor-link" href="#What-is-the-value-of-the-Slope-(b)-?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm</span><span class="o">.</span><span class="n">coef_</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="What-is-the-final-estimated-linear-model-we-get?">What is the final estimated linear model we get?<a class="anchor-link" href="#What-is-the-final-estimated-linear-model-we-get?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As we saw above, we should get a final linear model with the structure:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>\begin{equation*}
Yhat = a + b  X
\end{equation*}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Plugging in the actual values we get:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>price</strong> = 38423.31 - 821.73 x  <strong>highway-mpg</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-13(a):-Create-a-linear-regression-object?">Question 13(a): Create a linear regression object?<a class="anchor-link" href="#Question-13(a):-Create-a-linear-regression-object?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm1</span> <span class="o">=</span> <span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">lm1</span> 
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-13(b):-Train-the-model-using-'engine-size'-as-the-independent-variable-and-'price'-as-the-dependent-variable?">Question 13(b): Train the model using 'engine-size' as the independent variable and 'price' as the dependent variable?<a class="anchor-link" href="#Question-13(b):-Train-the-model-using-'engine-size'-as-the-independent-variable-and-'price'-as-the-dependent-variable?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">X</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s1">&#39;engine-size&#39;</span><span class="p">]]</span>
<span class="n">Y</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">]</span>
<span class="n">lm1</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span><span class="n">Y</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-13(c):-Find-the-slope-and-intercept-of-the-model?">Question 13(c): Find the slope and intercept of the model?<a class="anchor-link" href="#Question-13(c):-Find-the-slope-and-intercept-of-the-model?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Slope">Slope<a class="anchor-link" href="#Slope">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm1</span><span class="o">.</span><span class="n">coef_</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Intercept">Intercept<a class="anchor-link" href="#Intercept">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm1</span><span class="o">.</span><span class="n">intercept_</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-13(d):What-is-the-equation-of-the-predicted-line.-You-can-use-x-and-yhat-or-''engine-size'--or--'price'?&lt;/b&gt;">Question 13(d):What is the equation of the predicted line. You can use x and yhat or ''engine-size'  or  'price'?&lt;/b&gt;<a class="anchor-link" href="#Question-13(d):What-is-the-equation-of-the-predicted-line.-You-can-use-x-and-yhat-or-''engine-size'--or--'price'?&lt;/b&gt;">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Yhat=38423.31-821.733*X</p>
<p>Price=38423.31-821.733*engine-size</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.1.2-Multiple-Linear-Regression">4.1.2 Multiple Linear Regression<a class="anchor-link" href="#4.1.2-Multiple-Linear-Regression">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>What if we want to predict car price using more than one variable?</p>
<p>If we want to use more variables in our model to predict car price, we can use <strong>Multiple Linear Regression</strong>.
Multiple Linear Regression is very similar to Simple Linear Regression, but this method is used to explain the relationship between one continuous response (dependent) variable and <em>two or more</em> predictor (independent) variables.
Most of the real-world regression models involve multiple predictors. We illustrate the structure by using four predictor variables, but these results can generalize to any integer :</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>\begin{equation*}
Y: Response \ Variable\\
X_1 :Predictor\ Variable \ 1\\
X_2: Predictor\ Variable \ 2\\
X_3: Predictor\ Variable \ 3\\
X_4: Predictor\ Variable \ 4\\
\end{equation*}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>\begin{equation*}
a: intercept\\
b_1 :coefficients \ of\ Variable \ 1\\
b_2: coefficients \ of\ Variable \ 2\\
b_3: coefficients \ of\ Variable \ 3\\
b_4: coefficients \ of\ Variable \ 4\\
\end{equation*}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The equation is given by</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>\begin{equation*}
Yhat = a + b_1 X_1 + b_2 X_2 + b_3 X_3 + b_4 X_4
\end{equation*}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>From the previous section  we know that other good predictors of price could be:</p>
<ul>
<li>Horsepower</li>
<li>Curb-weight</li>
<li>Engine-size</li>
<li>Highway-mpg</li>
</ul>
<p>Let's develop a model using these variables as the predictor variables.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Z</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]]</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Fit the linear model using the four above-mentioned variables.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span> <span class="n">lm</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">Z</span><span class="p">,</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>What is the value of the intercept(a)?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm</span><span class="o">.</span><span class="n">intercept_</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>What are the values of the coefficients (b1, b2, b3, b4) ?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm</span><span class="o">.</span><span class="n">coef_</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>What is the final estimated linear model that we get?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As we saw above, we should get a final linear function with the structure:</p>
<p>\begin{equation*}
Yhat = a + b_1 X_1 + b_2 X_2 + b_3 X_3 + b_4 X_4
\end{equation*}</p>
<p>What is the linear function we get in this example?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Price</strong> = -15678.742628061467 + 52.65851272 x <strong>horsepower</strong> + 4.69878948 x <strong>curb-weight</strong> + 81.95906216 x <strong>engine-size</strong> + 33.58258185 x <strong>highway-mpg</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-14(a):-Create-and-train-a--Multiple-Linear-Regression-model-&quot;lm2&quot;-where-the-response-variable-is-price,-and-the-predictor-variable-is--'normalized-losses'-and--'highway-mpg'.">Question 14(a): Create and train a  Multiple Linear Regression model "lm2" where the response variable is price, and the predictor variable is  'normalized-losses' and  'highway-mpg'.<a class="anchor-link" href="#Question-14(a):-Create-and-train-a--Multiple-Linear-Regression-model-&quot;lm2&quot;-where-the-response-variable-is-price,-and-the-predictor-variable-is--'normalized-losses'-and--'highway-mpg'.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">LinearRegression</span>
<span class="n">lm2</span> <span class="o">=</span> <span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">lm2</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;normalized-losses&#39;</span> <span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]],</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="n">lm2</span><span class="o">.</span><span class="n">coef_</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-14(b):-Find-the-coefficient-of-the-model?">Question 14(b): Find the coefficient of the model?<a class="anchor-link" href="#Question-14(b):-Find-the-coefficient-of-the-model?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>lm2.coef_</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.2--Model-Evaluation-using-Visualization">4.2  Model Evaluation using Visualization<a class="anchor-link" href="#4.2--Model-Evaluation-using-Visualization">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we've developed some models, how do we evaluate our models and how do we choose the best one? One way to do this is by using visualization.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>import the visualization package: seaborn</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># import the visualization package: seaborn</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="o">%</span><span class="k">matplotlib</span> inline 
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.2.1-Regression-Plot">4.2.1 Regression Plot<a class="anchor-link" href="#4.2.1-Regression-Plot">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>When it comes to simple linear regression, an excellent way to visualise the fit of our model is by using <strong>regression plots</strong>.</p>
<p>This plot will show a combination of a scattered data points (a <strong>scatterplot</strong>), as well as the fitted <strong>linear regression</strong> line going through the data. This will give us a reasonable estimate of the relationship between the two variables, the strength of the correlation, as well as the direction (positive or negative correlation).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's visualize Horsepower as potential predictor variable of price:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">width</span> <span class="o">=</span> <span class="mi">12</span>
<span class="n">height</span> <span class="o">=</span> <span class="mi">10</span>
<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="n">width</span><span class="p">,</span> <span class="n">height</span><span class="p">))</span>
<span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;highway-mpg&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylim</span><span class="p">(</span><span class="mi">0</span><span class="p">,)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can see from this plot that price is negatively correlated to highway-mpg, since the regression slope is negative.
One thing to keep in mind when looking at a regression plot is to pay attention to how scattered the data points are around the regression line. This will give you a good indication of the variance of the data, and whether a linear model would be the best fit or not. If the data is too far off from the line, this linear model might not be the best model for this data. Let's compare this plot to the regression plot of "peak-rpm".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="n">width</span><span class="p">,</span> <span class="n">height</span><span class="p">))</span>
<span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;peak-rpm&quot;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s2">&quot;price&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylim</span><span class="p">(</span><span class="mi">0</span><span class="p">,)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Comparing the regression plot of "peak-rpm" and "highway-mpg" We see that the points for "highway-mpg" are much closer to the generated line and on the average decrease. The points for "peak-rpm"  have more spread around the predicted line, and it is much harder to determine if the points are decreasing or increasing as the  "highway-mpg"  increases.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-15:-Given-the-regression-plots-above-is-&quot;peak-rpm&quot;-or-&quot;highway-mpg&quot;--more-strongly-correlated-with-&quot;price&quot;.-Use-the-method--&quot;.corr()&quot;--to-verify-your-answer.">Question 15: Given the regression plots above is "peak-rpm" or "highway-mpg"  more strongly correlated with "price". Use the method  ".corr()"  to verify your answer.<a class="anchor-link" href="#Question-15:-Given-the-regression-plots-above-is-&quot;peak-rpm&quot;-or-&quot;highway-mpg&quot;--more-strongly-correlated-with-&quot;price&quot;.-Use-the-method--&quot;.corr()&quot;--to-verify-your-answer.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s2">&quot;peak-rpm&quot;</span><span class="p">,</span><span class="s2">&quot;highway-mpg&quot;</span><span class="p">,</span><span class="s2">&quot;price&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">corr</span><span class="p">()</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.2.2-Residual-Plot">4.2.2 Residual Plot<a class="anchor-link" href="#4.2.2-Residual-Plot">&#182;</a></h3><p>A good way to visualize the variance of the data is to use a residual plot.</p>
<p>What is a <strong>residual</strong>?</p>
<p>The difference between the observed value (y) and the predicted value (Yhat) is called the residual (e). When we look at a regression plot, the residual is the distance from the data point to the fitted regression line.</p>
<p>So what is a <strong>residual plot</strong>?</p>
<p>A residual plot is a graph that shows the residuals on the vertical y-axis and the independent variable on the horizontal x-axis.</p>
<p>What do we pay attention to when looking at a residual plot?</p>
<p>We look at the spread of the residuals:</p>
<ul>
<li>If the points in a residual plot are <strong>randomly spread out around the x-axis</strong>, then a <strong>linear model is appropriate</strong> for the data. Why is that? Randomly spread out residuals means that the variance is constant, and thus the linear model is a good fit for this data.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">width</span> <span class="o">=</span> <span class="mi">12</span>
<span class="n">height</span> <span class="o">=</span> <span class="mi">10</span>
<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="n">width</span><span class="p">,</span> <span class="n">height</span><span class="p">))</span>
<span class="n">sns</span><span class="o">.</span><span class="n">residplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;highway-mpg&#39;</span><span class="p">],</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><em>What is this plot telling us?</em></p>
<p>We can see from this residual plot that the residuals are not randomly spread around the x-axis, which leads us to believe that maybe a non-linear model is more appropriate for this data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.2.3-Multiple-Linear-Regression">4.2.3 Multiple Linear Regression<a class="anchor-link" href="#4.2.3-Multiple-Linear-Regression">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>How do we visualise a model for Multiple Linear Regression? This gets a bit more complicated because you can't visualise it with regression or residual plot.</p>
<p>One way to look at the fit of the model is by looking at the <strong>distribution plot</strong>: We can look at the distribution of the fitted values that result from the model and compare it to the distribution of the actual values.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>First lets make a prediction</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Y_hat</span> <span class="o">=</span> <span class="n">lm</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">Z</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="n">width</span><span class="p">,</span> <span class="n">height</span><span class="p">))</span>


<span class="n">ax1</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">hist</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s2">&quot;r&quot;</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s2">&quot;Actual Value&quot;</span><span class="p">)</span>
<span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">Yhat</span><span class="p">,</span> <span class="n">hist</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s2">&quot;b&quot;</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s2">&quot;Fitted Values&quot;</span> <span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax1</span><span class="p">)</span>


<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Actual vs Fitted Values for Price&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Price (in dollars)&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Proportion of Cars&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
<span class="n">plt</span><span class="o">.</span><span class="n">close</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can see that the fitted values are reasonably close to the actual values, since the two distributions overlap a bit. However, there is definitely some room for improvement.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.3-Polynomial-Regression-and-Pipelines">4.3 Polynomial Regression and Pipelines<a class="anchor-link" href="#4.3-Polynomial-Regression-and-Pipelines">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Polynomial regression</strong> is a particular case of the general linear regression model or multiple linear regression models. 
We get non-linear relationships by squaring or setting higher-order terms of the predictor variables.</p>
<p>There are different orders of polynomial regression:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<center>**Quadratic - 2nd order**</center><p>\begin{equation*}
Yhat = a + b_1 X^2 +b_2 X^2 
\\
\end{equation*}</p>
<center>**Cubic - 3rd order**</center><p>\begin{equation*}
Yhat = a + b_1 X^2 +b_2 X^2 +b_3 X^3\\
\end{equation*}</p>
<center> **Higher order**:</center><p>\begin{equation*}
Y = a + b_1 X^2 +b_2 X^2 +b_3 X^3 ....\\
\end{equation*}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We saw earlier that a linear model did not provide the best fit while using highway-mpg as the predictor variable. Let's see if we can try fitting a polynomial model to the data instead.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We will use the following function to plot the data:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">PlotPolly</span><span class="p">(</span><span class="n">model</span><span class="p">,</span><span class="n">independent_variable</span><span class="p">,</span><span class="n">dependent_variabble</span><span class="p">,</span> <span class="n">Name</span><span class="p">):</span>
    <span class="n">x_new</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">linspace</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">55</span><span class="p">,</span> <span class="mi">100</span><span class="p">)</span>
    <span class="n">y_new</span> <span class="o">=</span> <span class="n">model</span><span class="p">(</span><span class="n">x_new</span><span class="p">)</span>

   <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">independent_variable</span><span class="p">,</span><span class="n">dependent_variabble</span><span class="p">,</span><span class="s1">&#39;.&#39;</span><span class="p">,</span> <span class="n">x_new</span><span class="p">,</span> <span class="n">y_new</span><span class="p">,</span> <span class="s1">&#39;-&#39;</span><span class="p">)</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Polynomial Fit with Matplotlib for Price ~ Length&#39;</span><span class="p">)</span>
   <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">gca</span><span class="p">()</span>
   
   <span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">gcf</span><span class="p">()</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="n">Name</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Price of Cars&#39;</span><span class="p">)</span>

   <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">close</span><span class="p">()</span>
    
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;done&quot;</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>lets get the variables</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;highway-mpg&#39;</span><span class="p">]</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">]</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;done&quot;</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's fit the polynomial using the function <strong>polyfit</strong>, then use the function <strong>poly1d</strong> to display the polynomial function.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Here we use a polynomial of the 3rd order (cubic) </span>
<span class="n">f</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">polyfit</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
<span class="n">p</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">poly1d</span><span class="p">(</span><span class="n">f</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">p</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's plot the function</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">PlotPolly</span><span class="p">(</span><span class="n">p</span><span class="p">,</span><span class="n">x</span><span class="p">,</span><span class="n">y</span><span class="p">,</span> <span class="p">[</span><span class="s1">&#39;highway-mpg&#39;</span><span class="p">])</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">np</span><span class="o">.</span><span class="n">polyfit</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can already see from plotting that this polynomial model performs better than the linear model. This is because the generated polynomial function  "hits" more of the data points.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-16:-Create--11-order-polynomial-model-with-the-variables-x-and-y-from-above?">Question 16: Create  11 order polynomial model with the variables x and y from above?<a class="anchor-link" href="#Question-16:-Create--11-order-polynomial-model-with-the-variables-x-and-y-from-above?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># calculate polynomial</span>
<span class="c1"># Here we use a polynomial of the 3rd order (cubic) </span>
<span class="n">f1</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">polyfit</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="mi">11</span><span class="p">)</span>
<span class="n">p1</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">poly1d</span><span class="p">(</span><span class="n">f1</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">p</span><span class="p">)</span>
<span class="n">PlotPolly</span><span class="p">(</span><span class="n">p1</span><span class="p">,</span><span class="n">x</span><span class="p">,</span><span class="n">y</span><span class="p">,</span> <span class="s1">&#39;Length&#39;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The analytical expression for Multivariate Polynomial function gets complicated. For example, the expression for a second-order (degree=2)polynomial with two variables is given by:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
\begin{equation*}
Yhat = a + b_1 X_1 +b_2 X_2 +b_3 X_1 X_2+b_4 X_1^2+b_5 X_2^2
\end{equation*}
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can perform a polynomial transform on multiple features. First, we import the  module:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="k">import</span> <span class="n">PolynomialFeatures</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We create a <strong>PolynomialFeatures</strong> object of degree 2:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pr</span><span class="o">=</span><span class="n">PolynomialFeatures</span><span class="p">(</span><span class="n">degree</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
<span class="n">pr</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Z_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">Z</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The original data is of 201 samples and 4 features</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Z</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>after the transformation, there 201 samples and 15 features</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Z_pr</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.3.1-Pipeline">4.3.1 Pipeline<a class="anchor-link" href="#4.3.1-Pipeline">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Data Pipelines simplify the steps of processing the data. We use the module  <strong>Pipeline</strong> to create a pipeline. We also use <strong>StandardScaler</strong> as a step in our pipeline.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.pipeline</span> <span class="k">import</span> <span class="n">Pipeline</span>
<span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="k">import</span> <span class="n">StandardScaler</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We create the pipeline, by creating a list of tuples including the name of the model or estimator and its corresponding constructor.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Input</span><span class="o">=</span><span class="p">[(</span><span class="s1">&#39;scale&#39;</span><span class="p">,</span><span class="n">StandardScaler</span><span class="p">()),(</span><span class="s1">&#39;polynomial&#39;</span><span class="p">,</span> <span class="n">PolynomialFeatures</span><span class="p">(</span><span class="n">include_bias</span><span class="o">=</span><span class="kc">False</span><span class="p">)),(</span><span class="s1">&#39;model&#39;</span><span class="p">,</span><span class="n">LinearRegression</span><span class="p">())]</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we input the list as an argument to the pipeline constructor</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pipe</span><span class="o">=</span><span class="n">Pipeline</span><span class="p">(</span><span class="n">Input</span><span class="p">)</span>
<span class="n">pipe</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can normalize the data,  perform a transform and fit the model simultaneously.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pipe</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">Z</span><span class="p">,</span><span class="n">y</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Similarly,  we can normalize the data, perform a transform and produce a prediction  simultaneously</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ypipe</span><span class="o">=</span><span class="n">pipe</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">Z</span><span class="p">)</span>
<span class="n">ypipe</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-17:-Create-a-pipeline-that-Standardizes-the-data,-then-perform-prediction-using-a-linear-regression-model-using-the-features-Z-and-targets-y">Question 17: Create a pipeline that Standardizes the data, then perform prediction using a linear regression model using the features Z and targets y<a class="anchor-link" href="#Question-17:-Create-a-pipeline-that-Standardizes-the-data,-then-perform-prediction-using-a-linear-regression-model-using-the-features-Z-and-targets-y">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Input</span><span class="o">=</span><span class="p">[(</span><span class="s1">&#39;scale&#39;</span><span class="p">,</span><span class="n">StandardScaler</span><span class="p">()),(</span><span class="s1">&#39;model&#39;</span><span class="p">,</span><span class="n">LinearRegression</span><span class="p">())]</span>

<span class="n">pipe</span><span class="o">=</span><span class="n">Pipeline</span><span class="p">(</span><span class="n">Input</span><span class="p">)</span>

<span class="n">pipe</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">Z</span><span class="p">,</span><span class="n">y</span><span class="p">)</span>

<span class="n">ypipe</span><span class="o">=</span><span class="n">pipe</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">Z</span><span class="p">)</span>
<span class="n">ypipe</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.4-Measures-for-In-Sample-Evaluation">4.4 Measures for In-Sample Evaluation<a class="anchor-link" href="#4.4-Measures-for-In-Sample-Evaluation">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>When evaluating our models, not only do we want to visualise the results, but we also want a quantitative measure to determine how accurate the model is.</p>
<p>Two very important measures that are often used in Statistics to determine the accuracy of a model are:</p>
<ul>
<li>R^2 / R-squared</li>
<li>Mean Squared Error (MSE)</li>
</ul>
<h3 id="4.1.1-R-squared">4.1.1 R-squared<a class="anchor-link" href="#4.1.1-R-squared">&#182;</a></h3><p>R squared, also known as the coefficient of determination, is a measure to indicate how close the data is to the fitted regression line.
The value of the R-squared is the percentage of variation of the response variable (y) that is explained by a linear model.</p>
<h3 id="4.4.2-Mean-Squared-Error-(MSE)">4.4.2 Mean Squared Error (MSE)<a class="anchor-link" href="#4.4.2-Mean-Squared-Error-(MSE)">&#182;</a></h3><p>The Mean Squared Error measures the average of the squares of errors, that is, the difference between actual value (y) and the estimated value (ŷ).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Model-1:-Simple-Linear-Regression">Model 1: Simple Linear Regression<a class="anchor-link" href="#Model-1:-Simple-Linear-Regression">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the R^2</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#highway_mpg_fit</span>
<span class="n">lm</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">Y</span><span class="p">)</span>
<span class="c1"># Find the R^2</span>
<span class="n">lm</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">Y</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can say that ~ 49.659% of the variation of the price is explained by this simple linear model "horsepower_fit".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the MSE</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can predict the output i.e., "yhat" using the predict method, where X is the input variable:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Yhat</span><span class="o">=</span><span class="n">lm</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">)</span>
<span class="n">Yhat</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">]</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>lets import the function <strong>mean_squared_error</strong> from the module <strong>metrics</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">mean_squared_error</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we compare the predicted results with the actual results</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#mean_squared_error(Y_true, Y_predict)</span>
<span class="n">mean_squared_error</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">Yhat</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Model-2:-Multiple-Linear-Regression">Model 2: Multiple Linear Regression<a class="anchor-link" href="#Model-2:-Multiple-Linear-Regression">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the R^2</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># fit the model </span>
<span class="n">lm</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">Z</span><span class="p">,</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
<span class="c1"># Find the R^2</span>
<span class="n">lm</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">Z</span><span class="p">,</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">])</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can say that ~ 80.896 % of the variation of price is explained by this multiple linear regression "multi_fit".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the MSE</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we produce a prediction</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Y_predict_multifit</span> <span class="o">=</span> <span class="n">lm</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">Z</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we compare the predicted results with the actual results</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mean_squared_error</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">Y_predict_multifit</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Model-3:-Polynomial-Fit">Model 3: Polynomial Fit<a class="anchor-link" href="#Model-3:-Polynomial-Fit">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's calculate the R^2</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>let’s import the function <strong>r2_score</strong> from the module <strong> metrics</strong> as we are using a different function</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">r2_score</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We apply the function to get the value of r^2</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">r_squared</span> <span class="o">=</span> <span class="n">r2_score</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">p</span><span class="p">(</span><span class="n">x</span><span class="p">))</span>
<span class="n">r_squared</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can say that ~ 67.419 % of the variation of price is explained by this polynomial fit</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="MSE">MSE<a class="anchor-link" href="#MSE">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can also calculate the MSE:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mean_squared_error</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">],</span> <span class="n">p</span><span class="p">(</span><span class="n">x</span><span class="p">))</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.5-Prediction-and-Decision-Making">4.5 Prediction and Decision Making<a class="anchor-link" href="#4.5-Prediction-and-Decision-Making">&#182;</a></h2><h3 id="Prediction">Prediction<a class="anchor-link" href="#Prediction">&#182;</a></h3><p>In the previous section, we trained the model using the method <strong>fit</strong>. Now we will use the method <strong>predict</strong> to produce a prediction.Lets import <strong>pyplot</strong> for plotting; we will also be using some functions from numpy.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="o">%</span><span class="k">matplotlib</span> inline 
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Create a  new input</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">new_input</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">100</span><span class="p">,</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Fit the model</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lm</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">Y</span><span class="p">)</span>
<span class="n">lm</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Produce a prediction</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">yhat</span><span class="o">=</span><span class="n">lm</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">new_input</span><span class="p">)</span>
<span class="n">yhat</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">5</span><span class="p">]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we can plot the data</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">new_input</span><span class="p">,</span><span class="n">yhat</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Decision-Making:-Determining-a-Good-Model-Fit">Decision Making: Determining a Good Model Fit<a class="anchor-link" href="#Decision-Making:-Determining-a-Good-Model-Fit">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we have visualized the different models, and generated the R-squared and MSE values for the fits, how do we determine a good model fit?</p>
<ul>
<li><em>What is a good R-squared value?</em></li>
</ul>
<p>When comparing models, <strong>the model with the higher R-squared value is a better fit</strong> for the data.</p>
<ul>
<li><em>What is a good MSE?</em></li>
</ul>
<p>When comparing models, <strong>the model with the smallest MSE value is a better fit</strong> for the data.#### Let's take a look at the values for the different models we get.</p>
<h4 id="Let's-take-a-look-at-the-values-for-the-different-models.">Let's take a look at the values for the different models.<a class="anchor-link" href="#Let's-take-a-look-at-the-values-for-the-different-models.">&#182;</a></h4><p>Simple Linear Regression: Using Highway-mpg as a Predictor Variable of Price.</p>
<ul>
<li>R-squared: 0.49659118843391759</li>
<li>MSE: 3.16 x10^7</li>
</ul>
<p>Multiple Linear Regression: Using Horsepower, Curb-weight, Engine-size, and Highway-mpg as Predictor Variables of Price.</p>
<ul>
<li>R-squared: 0.80896354913783497</li>
<li>MSE: 1.2 x10^7</li>
</ul>
<p>Polynomial Fit: Using Highway-mpg as a Predictor Variable of Price.</p>
<ul>
<li>R-squared: 0.6741946663906514</li>
<li>MSE: 2.05 x 10^7</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Simple-Linear-Regression-model-(SLR)-vs-Multiple-Linear-Regression-model-(MLR)">Simple Linear Regression model (SLR) vs Multiple Linear Regression model (MLR)<a class="anchor-link" href="#Simple-Linear-Regression-model-(SLR)-vs-Multiple-Linear-Regression-model-(MLR)">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Usually, the more variables you have, the better your model is at predicting, but this is not always true. Sometimes you may not have enough data, you may run into numerical problems, or many of the variables may not be useful and or even act as noise. As a result, you should always check the MSE and R^2.</p>
<p>So to be able to compare the results of the MLR vs SLR models, we look at a combination of both the R-squared and MSE to make the best conclusion about the fit of the model.</p>
<ul>
<li><strong>MSE </strong> 
The MSE of SLR is  3.16x10^7  while MLR has an MSE of 1.2 x10^7.  The MSE of MLR is much smaller. </li>
</ul>
<ul>
<li><strong>R-squared</strong>: 
In this case, we can also see that there is a big difference between the R-squared of the SLR and the R-squared of the MLR. The R-squared for the SLR (~0.497) is very small compared to the R-squared for the MLR (~0.809). </li>
</ul>
<p>This R-squared in combination with the MSE show that MLR seems like the better model fit in this case, compared to SLR.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Simple-Linear-Model-(SLR)-vs-Polynomial-Fit">Simple Linear Model (SLR) vs Polynomial Fit<a class="anchor-link" href="#Simple-Linear-Model-(SLR)-vs-Polynomial-Fit">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li><p><strong>MSE</strong>: We can see that Polynomial Fit brought down the MSE, since this MSE is smaller than the one from the SLR.</p>
</li>
<li><p><strong>R-squared</strong>: The R-squared for the Polyfit is larger than the R-squared for the SLR, so the Polynomial Fit also brought up the R-squared quite a bit.</p>
</li>
</ul>
<p>Since the Polynomial Fit resulted in a lower MSE and a higher R-squared, we can conclude that this was a better fit model than the simple linear regression for predicting Price with Highway-mpg as a predictor variable.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Multiple-Linear-Regression-(MLR)-vs-Polynomial-Fit">Multiple Linear Regression (MLR) vs Polynomial Fit<a class="anchor-link" href="#Multiple-Linear-Regression-(MLR)-vs-Polynomial-Fit">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li><strong>MSE</strong>: The MSE for the MLR is smaller than the MSE for the Polynomial Fit.</li>
<li><strong>R-squared</strong>: The R-squared for the MLR is also much larger than for the Polynomial Fit.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Comparing-these-three-models,-we-conclude-that-the-MLR-model-is-the-best-model-to-be-able-to-predict-price-from-our-dataset.-This-result-makes-sense,-since-we-have-27-variables-in-total,-and-we-know-that-more-than-one-of-those-variables-are-potential-predictors-of-the-final-car-price.">Comparing these three models, we conclude that the MLR model is the best model to be able to predict price from our dataset. This result makes sense, since we have 27 variables in total, and we know that more than one of those variables are potential predictors of the final car price.<a class="anchor-link" href="#Comparing-these-three-models,-we-conclude-that-the-MLR-model-is-the-best-model-to-be-able-to-predict-price-from-our-dataset.-This-result-makes-sense,-since-we-have-27-variables-in-total,-and-we-know-that-more-than-one-of-those-variables-are-potential-predictors-of-the-final-car-price.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="5.-Model-Evaluation-and-Refinement">5. Model Evaluation and Refinement<a class="anchor-link" href="#5.-Model-Evaluation-and-Refinement">&#182;</a></h1><p>We have built models and made predictions of vehicle prices. Now we will determine how accurate these predictions are.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>First lets only use numeric data</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">=</span><span class="n">df</span><span class="o">.</span><span class="n">_get_numeric_data</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Libraries for plotting</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="k">import</span> <span class="n">display</span>
<span class="kn">from</span> <span class="nn">IPython.html</span> <span class="k">import</span> <span class="n">widgets</span> 
<span class="kn">from</span> <span class="nn">IPython.display</span> <span class="k">import</span> <span class="n">display</span>
<span class="kn">from</span> <span class="nn">ipywidgets</span> <span class="k">import</span> <span class="n">interact</span><span class="p">,</span> <span class="n">interactive</span><span class="p">,</span> <span class="n">fixed</span><span class="p">,</span> <span class="n">interact_manual</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;done&quot;</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Functions-for-plotting">Functions for plotting<a class="anchor-link" href="#Functions-for-plotting">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">DistributionPlot</span><span class="p">(</span><span class="n">RedFunction</span><span class="p">,</span><span class="n">BlueFunction</span><span class="p">,</span><span class="n">RedName</span><span class="p">,</span><span class="n">BlueName</span><span class="p">,</span><span class="n">Title</span> <span class="p">):</span>
    <span class="n">width</span> <span class="o">=</span> <span class="mi">12</span>
    <span class="n">height</span> <span class="o">=</span> <span class="mi">10</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="n">width</span><span class="p">,</span> <span class="n">height</span><span class="p">))</span>

   <span class="n">ax1</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">RedFunction</span><span class="p">,</span> <span class="n">hist</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s2">&quot;r&quot;</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="n">RedName</span><span class="p">)</span>
   <span class="n">ax2</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">BlueFunction</span><span class="p">,</span> <span class="n">hist</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s2">&quot;b&quot;</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="n">BlueName</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax1</span><span class="p">)</span>

   <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="n">Title</span><span class="p">)</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Price (in dollars)&#39;</span><span class="p">)</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Proportion of Cars&#39;</span><span class="p">)</span>

   <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">close</span><span class="p">()</span>
    
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">PollyPlot</span><span class="p">(</span><span class="n">xtrain</span><span class="p">,</span><span class="n">xtest</span><span class="p">,</span><span class="n">y_train</span><span class="p">,</span><span class="n">y_test</span><span class="p">,</span><span class="n">lr</span><span class="p">,</span><span class="n">poly_transform</span><span class="p">):</span>
    <span class="n">width</span> <span class="o">=</span> <span class="mi">12</span>
    <span class="n">height</span> <span class="o">=</span> <span class="mi">10</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="n">width</span><span class="p">,</span> <span class="n">height</span><span class="p">))</span>
    
    
   <span class="c1">#training data </span>
   <span class="c1">#testing data </span>
   <span class="c1"># lr:  linear regression object </span>
   <span class="c1">#poly_transform:  polynomial transformation object </span>
 
  <span class="n">xmax</span><span class="o">=</span><span class="nb">max</span><span class="p">([</span><span class="n">xtrain</span><span class="o">.</span><span class="n">values</span><span class="o">.</span><span class="n">max</span><span class="p">(),</span><span class="n">xtest</span><span class="o">.</span><span class="n">values</span><span class="o">.</span><span class="n">max</span><span class="p">()])</span>

   <span class="n">xmin</span><span class="o">=</span><span class="nb">min</span><span class="p">([</span><span class="n">xtrain</span><span class="o">.</span><span class="n">values</span><span class="o">.</span><span class="n">min</span><span class="p">(),</span><span class="n">xtest</span><span class="o">.</span><span class="n">values</span><span class="o">.</span><span class="n">min</span><span class="p">()])</span>

  <span class="n">x</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="n">xmin</span><span class="p">,</span><span class="n">xmax</span><span class="p">,</span><span class="mf">0.1</span><span class="p">)</span>


   <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">xtrain</span><span class="p">,</span><span class="n">y_train</span><span class="p">,</span><span class="s1">&#39;ro&#39;</span><span class="p">  </span><span class="n">label</span><span class="o">=</span><span class="s1">&#39;Training Data&#39;</span><span class="p">)</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">xtest</span><span class="p">,</span><span class="n">y_test</span><span class="p">,</span><span class="s1">&#39;go&#39;</span><span class="p">,</span><span class="n">label</span><span class="o">=</span><span class="s1">&#39;Test Data&#39;</span><span class="p">)</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">x</span><span class="p">,</span><span class="n">lr</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">poly_transform</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">))),</span><span class="n">label</span><span class="o">=</span><span class="s1">&#39;Predicted Function&#39;</span><span class="p">)</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">ylim</span><span class="p">([</span><span class="o">-</span><span class="mi">10000</span><span class="p">,</span><span class="mi">60000</span><span class="p">])</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Price&#39;</span><span class="p">)</span>
   <span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref1"></a></p>
<h2 id="5.1-Training-and-Testing">5.1 Training and Testing<a class="anchor-link" href="#5.1-Training-and-Testing">&#182;</a></h2><p>An important step in testing your model is to split your data into training and testing data. We will place the target data <strong>price</strong> in a separate dataframe <strong>y</strong>:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">y_data</span><span class="o">=</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;price&#39;</span><span class="p">]</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>drop price data in x data</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x_data</span><span class="o">=</span><span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="s1">&#39;price&#39;</span><span class="p">,</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>now we randomly split our data into training and testing data  using the function <strong>train_test_split</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">train_test_split</span>


<span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">x_data</span><span class="p">,</span> <span class="n">y_data</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mf">0.15</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>


<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;number of test samples :&quot;</span><span class="p">,</span> <span class="n">x_test</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;number of training samples:&quot;</span><span class="p">,</span><span class="n">x_train</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">])</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The <strong>test_size</strong> parameter sets the proportion of data that is split into the testing set. In the above, the testing set is set to 10% of the total dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-18:-Use-the-function-&quot;train_test_split&quot;-to-split-up-the-data-set-such-that-40%-of-the-data-samples-will-be-utilized-for-testing,-set-the-parameter-&quot;random_state&quot;-equal-to-zero.-The-output-of-the-function-should-be-the-following:--&quot;x_train_1&quot;-,-&quot;x_test_1&quot;,-&quot;y_train_1&quot;-and--&quot;y_test_1&quot;.">Question 18: Use the function "train_test_split" to split up the data set such that 40% of the data samples will be utilized for testing, set the parameter "random_state" equal to zero. The output of the function should be the following:  "x_train_1" , "x_test_1", "y_train_1" and  "y_test_1".<a class="anchor-link" href="#Question-18:-Use-the-function-&quot;train_test_split&quot;-to-split-up-the-data-set-such-that-40%-of-the-data-samples-will-be-utilized-for-testing,-set-the-parameter-&quot;random_state&quot;-equal-to-zero.-The-output-of-the-function-should-be-the-following:--&quot;x_train_1&quot;-,-&quot;x_test_1&quot;,-&quot;y_train_1&quot;-and--&quot;y_test_1&quot;.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">x_data</span><span class="p">,</span> <span class="n">y_data</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mf">0.40</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's import <strong>LinearRegression</strong> from the module <strong>linear_model</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">LinearRegression</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We create a Linear Regression object:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lre</span><span class="o">=</span><span class="n">LinearRegression</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we fit the model using the feature horsepower</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lre</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span><span class="n">y_train</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's Calculate the R^2 on the test data:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lre</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span><span class="n">y_test</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we can see the R^2 is much smaller using the test data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lre</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span><span class="n">y_train</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-19:-Find-the-R^2--on-the-test-data-using-90%-of-the-data-for-training-data">Question 19: Find the R^2  on the test data using 90% of the data for training data<a class="anchor-link" href="#Question-19:-Find-the-R^2--on-the-test-data-using-90%-of-the-data-for-training-data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x_train1</span><span class="p">,</span> <span class="n">x_test1</span><span class="p">,</span> <span class="n">y_train1</span><span class="p">,</span> <span class="n">y_test1</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">x_data</span><span class="p">,</span> <span class="n">y_data</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span> <span class="mf">0.9</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span> <span class="mi">0</span><span class="p">)</span>
<span class="n">lre</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train1</span><span class="p">[[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">]],</span> <span class="n">y_train1</span><span class="p">)</span>
<span class="n">lre</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_test1</span><span class="p">[[</span><span class="s2">&quot;horsepower&quot;</span><span class="p">]],</span> <span class="n">y_test1</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Sometimes you do not have sufficient testing data; as a result, you may want to perform Cross-validation. Let's  go over several methods that you can use for  Cross-validation.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Cross-validation-Score">Cross-validation Score<a class="anchor-link" href="#Cross-validation-Score">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Lets import <strong>model_selection</strong> from the module <strong>cross_val_scor</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">cross_val_score</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;done&quot;</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We input the object, the feature in this case ' horsepower', the target data (y_data). The parameter 'cv'  determines the number of folds; in this case 4.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Rcross</span><span class="o">=</span><span class="n">cross_val_score</span><span class="p">(</span><span class="n">lre</span><span class="p">,</span><span class="n">x_data</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span> <span class="n">y_data</span><span class="p">,</span><span class="n">cv</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The default scoring is R^2; each element in the array has the average  R^2 value in the fold:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Rcross</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can calculate the average and standard deviation of our estimate:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The mean of the folds are&quot;</span><span class="p">,</span> <span class="n">Rcross</span><span class="o">.</span><span class="n">mean</span><span class="p">(),</span><span class="s2">&quot;and the standard deviation is&quot;</span> <span class="p">,</span><span class="n">Rcross</span><span class="o">.</span><span class="n">std</span><span class="p">())</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can use negative squared error as a score by setting the parameter  'scoring' metric to 'neg_mean_squared_error'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="o">-</span><span class="mi">1</span><span class="o">*</span><span class="n">cross_val_score</span><span class="p">(</span><span class="n">lre</span><span class="p">,</span><span class="n">x_data</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span> <span class="n">y_data</span><span class="p">,</span><span class="n">cv</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span><span class="n">scoring</span><span class="o">=</span><span class="s1">&#39;neg_mean_squared_error&#39;</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-20:-Calculate-the-average-R^2-using-two-folds,-find-the-average-R^2-for-the-second-fold-utilizing-the-horsepower-as-a-feature-:">Question 20: Calculate the average R^2 using two folds, find the average R^2 for the second fold utilizing the horsepower as a feature :<a class="anchor-link" href="#Question-20:-Calculate-the-average-R^2-using-two-folds,-find-the-average-R^2-for-the-second-fold-utilizing-the-horsepower-as-a-feature-:">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Rcross2</span> <span class="o">=</span> <span class="n">cross_val_score</span><span class="p">(</span><span class="n">lre</span><span class="p">,</span><span class="n">x_data</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span> <span class="n">y_data</span><span class="p">,</span> <span class="n">cv</span><span class="o">=</span> <span class="mi">2</span><span class="p">)</span>
<span class="n">Rcross2</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>You can also use the function 'cross_val_predict' to predict the output. The function splits up the data into the specified number of folds, using one fold to get a prediction while the rest of the folds are used as test data. First import the function:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">cross_val_predict</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We input the object, the feature in this case <strong>'horsepower'</strong> , the target data <strong>y_data</strong>. The parameter 'cv' determines the number of folds; in this case 4.  We can produce an output:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">yhat</span><span class="o">=</span><span class="n">cross_val_predict</span><span class="p">(</span><span class="n">lre</span><span class="p">,</span><span class="n">x_data</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span> <span class="n">y_data</span><span class="p">,</span><span class="n">cv</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
<span class="n">yhat</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">5</span><span class="p">]</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref2"></a></p>
<h2 id="5.2-Overfitting,-Underfitting-and-Model-Selection">5.2 Overfitting, Underfitting and Model Selection<a class="anchor-link" href="#5.2-Overfitting,-Underfitting-and-Model-Selection">&#182;</a></h2><p>It turns out that the test data sometimes referred to as the out of sample data is a much better measure of how well your model performs in the real world.  One reason for this is overfitting; let's go over some examples. It turns out these differences are more apparent in Multiple Linear Regression and Polynomial Regression so we will explore overfitting in that context.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's create Multiple linear regression objects and train the model using <strong>'horsepower'</strong>, <strong>'curb-weight'</strong>, <strong>'engine-size'</strong> and <strong>'highway-mpg'</strong> as features.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lr</span><span class="o">=</span><span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">lr</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]],</span><span class="n">y_train</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Prediction using training data:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">yhat_train</span><span class="o">=</span><span class="n">lr</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]])</span>
<span class="n">yhat_train</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">5</span><span class="p">]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Prediction using test data:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">yhat_test</span><span class="o">=</span><span class="n">lr</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]])</span>
<span class="n">yhat_test</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">5</span><span class="p">]</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's perform some model evaluation using our training and testing data separately. First  we import the seaborn and matplotlibb library for plotting.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="o">%</span><span class="k">matplotlib</span> inline
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's examine the distribution of the predicted values of the training data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Title</span><span class="o">=</span><span class="s1">&#39;Distribution  Plot of  Predicted Value Using Training Data vs Training Data Distribution &#39;</span>
<span class="n">DistributionPlot</span><span class="p">(</span><span class="n">y_train</span><span class="p">,</span><span class="n">yhat_train</span><span class="p">,</span><span class="s2">&quot;Actual Values (Train)&quot;</span><span class="p">,</span><span class="s2">&quot;Predicted Values (Train)&quot;</span><span class="p">,</span><span class="n">Title</span><span class="p">)</span>
</pre></div>

    
</di>v>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Figur 1: Plot of predicted values using the training data compared to the training data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>So far the model seems to be doing well in learning from the training dataset. But what happens when the model encounters new data from the testing dataset? When the model generates new values from the test data, we see the distribution of the predicted values is much different from the actual target values.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Title</span><span class="o">=</span><span class="s1">&#39;Distribution  Plot of  Predicted Value Using Test Data vs Data Distribution of Test Data&#39;</span>
<span class="n">DistributionPlot</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span><span class="n">yhat_test</span><span class="p">,</span><span class="s2">&quot;Actual Values (Test)&quot;</span><span class="p">,</span><span class="s2">&quot;Predicted Values (Test)&quot;</span><span class="p">,</span><span class="n">Title</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Figur 2: Plot of predicted value using the test data compared to the test data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Comparing Figure 1 and Figure 2; it is evident the distribution of the test data in Figure 1 is much better at fitting the data. This difference in Figure 2 is apparent where the ranges are from 5000 to 15 000. This is where the distribution shape is exceptionally different. Let's see if polynomial regression also exhibits a drop in the prediction accuracy when analysing the test dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="k">import</span> <span class="n">PolynomialFeatures</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;done&quot;</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Overfitting">Overfitting<a class="anchor-link" href="#Overfitting">&#182;</a></h4><p>Overfitting occurs when the model fits the noise, not the underlying process. Therefore when testing your model using the test-set, your model does not perform as well as it is modelling noise, not the underlying process that generated the relationship. Let's create a degree 5 polynomial model.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's use 55 percent of the data for testing and the rest for training:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">x_data</span><span class="p">,</span> <span class="n">y_data</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mf">0.45</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;done&quot;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We will perform a degree 5 polynomial transformation on the feature <strong>'horse power'</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pr</span><span class="o">=</span><span class="n">PolynomialFeatures</span><span class="p">(</span><span class="n">degree</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">x_train_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]])</span>
<span class="n">x_test_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]])</span>
<span class="n">pr</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now let's create a linear regression model "poly" and train it.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">poly</span><span class="o">=</span><span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">poly</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can see the output of our model using the method  "predict." then assign the values to "yhat".</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">yhat</span><span class="o">=</span><span class="n">poly</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">x_test_pr</span> <span class="p">)</span>
<span class="n">yhat</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">5</span><span class="p">]</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's take the first five predicted values and compare it to the actual targets.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Predicted values:&quot;</span><span class="p">,</span> <span class="n">yhat</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;True values:&quot;</span><span class="p">,</span><span class="n">y_test</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We will use the function "PollyPlot" that we defined at the beginning of the lab to display the training data, testing data, and the predicted function.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">PollyPlot</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span><span class="n">y_train</span><span class="p">,</span><span class="n">y_test</span><span class="p">,</span><span class="n">poly</span><span class="p">,</span><span class="n">pr</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Figur 4 A polynomial regression model, red dots represent training data, green dots represent test data, and the blue line represents the model prediction.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We see that the estimated function appears to track the data but around 200 horsepower, the function begins to diverge from the data points.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>R^2 of the training data:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">poly</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>R^2 of the test data:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">poly</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_test_pr</span><span class="p">,</span> <span class="n">y_test</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We see the R^2 for the training data is 0.5567 while the R^2 on the test data was -29.87.  The lower the R^2, the worse the model, a Negative R^2 is a sign of overfitting.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's see how the R^2 changes on the test data for different order polynomials and plot the results:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Rsqu_test</span><span class="o">=</span><span class="p">[]</span>

<span class="n">order</span><span class="o">=</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="mi">4</span><span class="p">]</span>
<span class="k">for</span> <span class="n">n</span> <span class="ow">in</span> <span class="n">order</span><span class="p">:</span>
    <span class="n">pr</span><span class="o">=</span><span class="n">PolynomialFeatures</span><span class="p">(</span><span class="n">degree</span><span class="o">=</span><span class="n">n</span><span class="p">)</span>
    
   <span class="n">x_train_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]])</span>
    
   <span class="n">x_test_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]])</span>    
    
  <span class="n">lr</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
    
   <span class="n">Rsqu_test</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">lr</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_test_pr</span><span class="p">,</span><span class="n">y_test</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">order</span><span class="p">,</span><span class="n">Rsqu_test</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;order&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;R^2&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;R^2 Using Test Data&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">text</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span> <span class="mf">0.75</span><span class="p">,</span> <span class="s1">&#39;Maximum R^2 &#39;</span><span class="p">)</span>    
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We see the R^2 gradually increases until an order three polynomial is used. Then the  R^2 dramatically decreases at four.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The following function will be used in the next section; please run the cell.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">f</span><span class="p">(</span><span class="n">order</span><span class="p">,</span><span class="n">test_data</span><span class="p">):</span>
    <span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">x_data</span><span class="p">,</span> <span class="n">y_data</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="n">test_data</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
    <span class="n">pr</span><span class="o">=</span><span class="n">PolynomialFeatures</span><span class="p">(</span><span class="n">degree</span><span class="o">=</span><span class="n">order</span><span class="p">)</span>
    <span class="n">x_train_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]])</span>
    <span class="n">x_test_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]])</span>
    <span class="n">poly</span><span class="o">=</span><span class="n">LinearRegression</span><span class="p">()</span>
    <span class="n">poly</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
    <span class="n">PollyPlot</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">]],</span><span class="n">y_train</span><span class="p">,</span><span class="n">y_test</span><span class="p">,</span><span class="n">poly</span><span class="p">,</span><span class="n">pr</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The following interface allows you to experiment with different polynomial orders and different amounts of data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">interact</span><span class="p">(</span><span class="n">f</span><span class="p">,</span> <span class="n">order</span><span class="o">=</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">6</span><span class="p">,</span><span class="mi">1</span><span class="p">),</span><span class="n">test_data</span><span class="o">=</span><span class="p">(</span><span class="mf">0.05</span><span class="p">,</span><span class="mf">0.95</span><span class="p">,</span><span class="mf">0.05</span><span class="p">))</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-21(a):-We-can-perform-polynomial-transformations-with-more-than-one-feature.-Create-a-&quot;PolynomialFeatures&quot;-object-&quot;pr1&quot;-of-degree-two.-?">Question 21(a): We can perform polynomial transformations with more than one feature. Create a "PolynomialFeatures" object "pr1" of degree two. ?<a class="anchor-link" href="#Question-21(a):-We-can-perform-polynomial-transformations-with-more-than-one-feature.-Create-a-&quot;PolynomialFeatures&quot;-object-&quot;pr1&quot;-of-degree-two.-?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pr1</span><span class="o">=</span><span class="n">PolynomialFeatures</span><span class="p">(</span><span class="n">degree</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-21(b):-Transform-the-training-and-testing-samples-for-the-features-'horsepower',-'curb-weight',-'engine-size'-and-'highway-mpg'.-Hint:-use-the-method-&quot;fit_transform&quot;">Question 21(b): Transform the training and testing samples for the features 'horsepower', 'curb-weight', 'engine-size' and 'highway-mpg'. Hint: use the method "fit_transform"<a class="anchor-link" href="#Question-21(b):-Transform-the-training-and-testing-samples-for-the-features-'horsepower',-'curb-weight',-'engine-size'-and-'highway-mpg'.-Hint:-use-the-method-&quot;fit_transform&quot;">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x_train_pr1</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]])</span>
<span class="n">x_test_pr1</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]])</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-21(c):-How-many-dimensions-does-the-new-feature-have?-Hint:-use-the-attribute-&quot;shape&quot;">Question 21(c): How many dimensions does the new feature have? Hint: use the attribute "shape"<a class="anchor-link" href="#Question-21(c):-How-many-dimensions-does-the-new-feature-have?-Hint:-use-the-attribute-&quot;shape&quot;">&#182;</a></h3>
</div>
</div>
</div>There are now 15 features: x_train_pr1.shape
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question--21(d):-Create-a-linear-regression-model-&quot;poly1&quot;-and-train-the-object-using-the-method-&quot;fit&quot;-using-the-polynomial-features?">Question  21(d): Create a linear regression model "poly1" and train the object using the method "fit" using the polynomial features?<a class="anchor-link" href="#Question--21(d):-Create-a-linear-regression-model-&quot;poly1&quot;-and-train-the-object-using-the-method-&quot;fit&quot;-using-the-polynomial-features?">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn</span> <span class="k">import</span> <span class="n">linear_model</span>
<span class="n">poly1</span><span class="o">=</span><span class="n">linear_model</span><span class="o">.</span><span class="n">LinearRegression</span><span class="p">()</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train_pr1</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question--21(e):-Use-the-method--&quot;predict&quot;-to-predict-an-output-on-the-polynomial-features,-then-use-the-function-&quot;DistributionPlot&quot;--to-display-the-distribution-of-the-predicted-output-vs-the-test-data?&lt;/b&gt;">Question  21(e): Use the method  "predict" to predict an output on the polynomial features, then use the function "DistributionPlot"  to display the distribution of the predicted output vs the test data?&lt;/b&gt;<a class="anchor-link" href="#Question--21(e):-Use-the-method--&quot;predict&quot;-to-predict-an-output-on-the-polynomial-features,-then-use-the-function-&quot;DistributionPlot&quot;--to-display-the-distribution-of-the-predicted-output-vs-the-test-data?&lt;/b&gt;">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">yhat_test1</span><span class="o">=</span><span class="n">poly1</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">x_train_pr1</span><span class="p">)</span>
<span class="n">Title</span><span class="o">=</span><span class="s1">&#39;Distribution  Plot of  Predicted Value Using Test Data vs Data Distribution of Test Data&#39;</span>
<span class="n">DistributionPlot</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span><span class="n">yhat_test1</span><span class="p">,</span><span class="s2">&quot;Actual Values (Test)&quot;</span><span class="p">,</span><span class="s2">&quot;Predicted Values (Test)&quot;</span><span class="p">,</span><span class="n">Title</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-21(f):-Use-the-distribution-plot-to-determine-the-two-regions-were-the-predicted-prices-are-less-accurate-than-the-actual-prices.">Question 21(f): Use the distribution plot to determine the two regions were the predicted prices are less accurate than the actual prices.<a class="anchor-link" href="#Question-21(f):-Use-the-distribution-plot-to-determine-the-two-regions-were-the-predicted-prices-are-less-accurate-than-the-actual-prices.">&#182;</a></h3>
</div>
</div>
</div>The predicted value is lower than actual value for cars where the price  $ 10,000 range, conversely the predicted price is larger than the price cost in the $30, 000 to $40,000 range. As such the model is not as accurate in these ranges 
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>&lt;img src= "<a href="https://ibm.box.com/shared/static/c35ipv9zeanu7ynsnppb8gjo2re5ugeg.png">https://ibm.box.com/shared/static/c35ipv9zeanu7ynsnppb8gjo2re5ugeg.png</a>" width = "700" /, align = "center"&gt;</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref3"></a></p>
<h2 id="5.3-Ridge-regression">5.3 Ridge regression<a class="anchor-link" href="#5.3-Ridge-regression">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In this section, we will review Ridge Regression we will see how the parameter Alfa changes the model. Just a note here our test data will be used as validation data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's perform a degree two polynomial transformation on our data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pr</span><span class="o">=</span><span class="n">PolynomialFeatures</span><span class="p">(</span><span class="n">degree</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
<span class="n">x_train_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_train</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">,</span><span class="s1">&#39;normalized-losses&#39;</span><span class="p">,</span><span class="s1">&#39;symboling&#39;</span><span class="p">]])</span>
<span class="n">x_test_pr</span><span class="o">=</span><span class="n">pr</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">,</span><span class="s1">&#39;normalized-losses&#39;</span><span class="p">,</span><span class="s1">&#39;symboling&#39;</span><span class="p">]])</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's import  <strong>Ridge</strong>  from the module <strong>linear models</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">Ridge</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's create a Ridge regression object, setting the regularization parameter to 0.1</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">RigeModel</span><span class="o">=</span><span class="n">Ridge</span><span class="p">(</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.1</span><span class="p">)</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Like regular regression, you can fit the model using the method <strong>fit</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">RigeModel</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Similarly, you can obtain a prediction:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">yhat</span><span class="o">=</span><span class="n">RigeModel</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">x_test_pr</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's compare the first five predicted samples to our test set</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s1">&#39;predicted:&#39;</span><span class="p">,</span> <span class="n">yhat</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;test set :&#39;</span><span class="p">,</span> <span class="n">y_test</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We select the value of Alfa that minimizes the test error, for example, we can use a for loop.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Rsqu_test</span><span class="o">=</span><span class="p">[]</span>
<span class="n">Rsqu_train</span><span class="o">=</span><span class="p">[]</span>
<span class="n">dummy1</span><span class="o">=</span><span class="p">[]</span>
<span class="n">ALFA</span><span class="o">=</span><span class="mi">5000</span><span class="o">*</span><span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">10000</span><span class="p">))</span>
<span class="k">for</span> <span class="n">alfa</span> <span class="ow">in</span> <span class="n">ALFA</span><span class="p">:</span>
    <span class="n">RigeModel</span><span class="o">=</span><span class="n">Ridge</span><span class="p">(</span><span class="n">alpha</span><span class="o">=</span><span class="n">alfa</span><span class="p">)</span> 
    <span class="n">RigeModel</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
    <span class="n">Rsqu_test</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">RigeModel</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_test_pr</span><span class="p">,</span><span class="n">y_test</span><span class="p">))</span>
    <span class="n">Rsqu_train</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">RigeModel</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span><span class="n">y_train</span><span class="p">))</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can plot out the value of R^2 for different Alphas</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">width</span> <span class="o">=</span> <span class="mi">12</span>
<span class="n">height</span> <span class="o">=</span> <span class="mi">10</span>
<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="n">width</span><span class="p">,</span> <span class="n">height</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">ALFA</span><span class="p">,</span><span class="n">Rsqu_test</span><span class="p">,</span><span class="n">label</span><span class="o">=</span><span class="s1">&#39;validation data  &#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">ALFA</span><span class="p">,</span><span class="n">Rsqu_train</span><span class="p">,</span><span class="s1">&#39;r&#39;</span><span class="p">,</span><span class="n">label</span><span class="o">=</span><span class="s1">&#39;training Data &#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;alpha&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;R^2&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Figure 6:The blue line represents the R^2 of the test data, and the red line represents the R^2 of the training data. The x-axis represents the different values of Alfa</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The red line in figure 6 represents the  R^2 of the test data, as Alpha increases the R^2 decreases; therefore as Alfa increases the model performs worse on the test data.  The blue line represents the R^2 on the validation data, as the value for Alfa increases the R^2 decreases.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-22:-Perform-Ridge-regression-and-calculate-the-R^2-using-the-polynomial-features,-use-the-training-data-to-train-the-model-and-test-data-to-test-the-model.-The-parameter-alpha-should-be-set-to--10.">Question 22: Perform Ridge regression and calculate the R^2 using the polynomial features, use the training data to train the model and test data to test the model. The parameter alpha should be set to  10.<a class="anchor-link" href="#Question-22:-Perform-Ridge-regression-and-calculate-the-R^2-using-the-polynomial-features,-use-the-training-data-to-train-the-model-and-test-data-to-test-the-model.-The-parameter-alpha-should-be-set-to--10.">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">RigeModel</span><span class="o">=</span><span class="n">Ridge</span><span class="p">(</span><span class="n">alpha</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span> 
<span class="n">RigeModel</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train_pr</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
<span class="n">RigeModel</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_test_pr</span><span class="p">,</span> <span class="n">y_test</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a id="ref4"></a></p>
<h2 id="5.4-Grid-Search">5.4 Grid Search<a class="anchor-link" href="#5.4-Grid-Search">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The term Alfa is a hyperparameter, sklearn has the class  <strong>GridSearchCV</strong> to make the process of finding the best hyperparameter simpler.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's import <strong>GridSearchCV</strong> from  the module <strong>model_selection</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">GridSearchCV</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;done&quot;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We create a dictionary of parameter values:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">parameters1</span><span class="o">=</span> <span class="p">[{</span><span class="s1">&#39;alpha&#39;</span><span class="p">:</span> <span class="p">[</span><span class="mf">0.001</span><span class="p">,</span><span class="mf">0.1</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">100</span><span class="p">,</span> <span class="mi">1000</span><span class="p">,</span><span class="mi">10000</span><span class="p">,</span><span class="mi">100000</span><span class="p">,</span><span class="mi">100000</span><span class="p">]}]</span>
<span class="n">parameters1</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Create a ridge regions object:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">RR</span><span class="o">=</span><span class="n">Ridge</span><span class="p">()</span>
<span class="n">RR</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Create a ridge grid search object</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Grid1</span> <span class="o">=</span> <span class="n">GridSearchCV</span><span class="p">(</span><span class="n">RR</span><span class="p">,</span> <span class="n">parameters1</span><span class="p">,</span><span class="n">cv</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Fit the model</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Grid1</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_data</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]],</span><span class="n">y_data</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The object finds the best parameter values on the validation data. We can obtain the estimator with the best parameters and assign it to the variable BestRR as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">BestRR</span><span class="o">=</span><span class="n">Grid1</span><span class="o">.</span><span class="n">best_estimator_</span>
<span class="n">BestRR</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We now test our model on the test data</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">BestRR</span><span class="o">.</span><span class="n">score</span><span class="p">(</span><span class="n">x_test</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]],</span><span class="n">y_test</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Question-23:-Perform-a-grid-search-for-the-alpha-parameter-and-the-normalization-parameter,-then-find-the-best-values-of-the-parameters">Question 23: Perform a grid search for the alpha parameter and the normalization parameter, then find the best values of the parameters<a class="anchor-link" href="#Question-23:-Perform-a-grid-search-for-the-alpha-parameter-and-the-normalization-parameter,-then-find-the-best-values-of-the-parameters">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">parameters2</span><span class="o">=</span> <span class="p">[{</span><span class="s1">&#39;alpha&#39;</span><span class="p">:</span> <span class="p">[</span><span class="mf">0.001</span><span class="p">,</span><span class="mf">0.1</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">100</span><span class="p">,</span> <span class="mi">1000</span><span class="p">,</span><span class="mi">10000</span><span class="p">,</span><span class="mi">100000</span><span class="p">,</span><span class="mi">100000</span><span class="p">],</span><span class="s1">&#39;normalize&#39;</span><span class="p">:[</span><span class="kc">True</span><span class="p">,</span><span class="kc">False</span><span class="p">]}</span> <span class="p">]</span>
<span class="n">Grid2</span> <span class="o">=</span> <span class="n">GridSearchCV</span><span class="p">(</span><span class="n">Ridge</span><span class="p">(),</span> <span class="n">parameters2</span><span class="p">,</span><span class="n">cv</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
<span class="n">Grid2</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_data</span><span class="p">[[</span><span class="s1">&#39;horsepower&#39;</span><span class="p">,</span> <span class="s1">&#39;curb-weight&#39;</span><span class="p">,</span> <span class="s1">&#39;engine-size&#39;</span><span class="p">,</span> <span class="s1">&#39;highway-mpg&#39;</span><span class="p">]],</span><span class="n">y_data</span><span class="p">)</span>
<span class="n">Grid2</span><span class="o">.</span><span class="n">best_estimator_</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="About-the-Authors:">About the Authors:<a class="anchor-link" href="#About-the-Authors:">&#182;</a></h1><p>This notebook written <a href="https://www.linkedin.com/in/joseph-s-50398b136/">Joseph Santarcangelo PhD</a>,<a href="https://www.linkedin.com/in/mahdi-noorian-58219234/">Mahdi Noorian PhD</a>, Bahare Talayian, Eric Xiao, Steven Dong, Parizad , Hima Vsudevan, <a href="https://www.linkedin.com/in/fiorellawever/">Fiorella Wenver</a> and edited by <a href="https://www.linkedin.com/in/gokulrs/">Gokul R S</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Recommended,-Python-for-Data-Science-click-to-start-course:">Recommended, Python for Data Science click to start course:<a class="anchor-link" href="#Recommended,-Python-for-Data-Science-click-to-start-course:">&#182;</a></h4><p><a href="http://cocl.us/DA0101ENtoPY0101EN">
    <img src="https://ibm.box.com/shared/static/jmtb4pgle2dsdlzfmyrgv755cnqw95wk.png" width ="100" /, align = "Left"></a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Copyright &copy; 2017 <a href="cognitiveclass.ai?utm_source=bducopyrightlink&amp;utm_medium=dswb&amp;utm_campaign=bdu">cognitiveclass.ai</a>. This notebook and its source code are released under the terms of the <a href="https://bigdatauniversity.com/mit-license/">MIT License</a>.</p>

</div>
</div>
</div>
    </div>
  </div>
</body>
</html>
