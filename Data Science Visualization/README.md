<h1 align=center><font size = 7>Data Visualization with Python </font></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="(Project-Immigration-to-Canada-from-1980-to-2013)">(Project-Immigration to Canada from 1980 to 2013)<a class="anchor-link" href="#(Project-Immigration-to-Canada-from-1980-to-2013)">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Introduction">Introduction<a class="anchor-link" href="#Introduction">&#182;</a></h2><p>The aim of this project to introduce you to data visualization with Python as concrete and as consistent as possible. 
Speaking of consistency, because there is no <em>best</em> data visualization library avaiblable for Python, we have to introduce different libraries and show their benefits when we are discussing new visualization concepts. Doing so, we can able to judge and decide on the best visualitzation technique and tool for a given problem.</p>
<p><strong>Note</strong>: The majority of the plots and visualizations will be generated using data stored in <em>pandas</em> dataframes.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Table-of-Contents">Table of Contents<a class="anchor-link" href="#Table-of-Contents">&#182;</a></h2><div class="alert alert-block alert-info" style="margin-top: 20px">

1. Exploring Datasets with *Pandas*<br>
1.1 The Dataset: Immigration to Canada from 1980 to 2013<br>
1.2 *Pandas* Basics<br>
1.3 *Pandas* Intermediate: Indexing and Selection <br>
2. Visualizing Data using Matplotlib<br>
2.1 Matplotlib: Standard Python Visualization Library<br>
2.2 Line Plots<br>
2.3 Pie Charts<br>
2.4 Box Plots <br>
2.5 Scatter Plots<br>
2.6 Bubble Plots<br> 
2.7 Area Plots<br>
2.8 Histogram <br>
2.9 Bar Charts <br>
2.10 Waffle Charts <br>
3. Visualizing Data using word cloud <br>
    3.1 Word Clouds <br>
4. Visualizing Data using Seaborn<br>
4.1 Regression Plots <br> 
5. Generating Maps with Python <br>
    5.1 Exploring Datasets with *Pandas* <br>
    5.2 Downloading and Prepping Data <br>
    5.3 Introduction to Folium <br>
    5.4 Map with Markers <br>
    5.5 Choropleth Maps <br>
</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="1. Exploring-Datasets-with-pandas-">1. Exploring Datasets with <em>pandas</em> <a id="0" /><a class="anchor-link" href="#1. Exploring-Datasets-with-pandas-">&#182;</a></h1><p><em>pandas</em> is an essential data analysis toolkit for Python. From their <a href="http://pandas.pydata.org/">website</a>:</p>
<blockquote><p><em>pandas</em> is a Python package providing fast, flexible, and expressive data structures designed to make working with “relational” or “labeled” data both easy and intuitive. It aims to be the fundamental high-level building block for doing practical, <strong>real world</strong> data analysis in Python.</p>
</blockquote>
<p>The course heavily relies on <em>pandas</em> for data wrangling, analysis, and visualization. We encourage you to spend some time and  familizare yourself with the <em>pandas</em> API Reference: <a href="http://pandas.pydata.org/pandas-docs/stable/api.html">http://pandas.pydata.org/pandas-docs/stable/api.html</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="1.1 The-Dataset:-Immigration-to-Canada-from-1980-to-2013-">1.1 The Dataset: Immigration to Canada from 1980 to 2013 <a id="2" /><a class="anchor-link" href="#1.1 The-Dataset:-Immigration-to-Canada-from-1980-to-2013-">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Dataset Source: <a href="http://www.un.org/en/development/desa/population/migration/data/empirical2/migrationflows.shtml">International migration flows to and from selected countries - The 2015 revision</a>.</p>
<p>The dataset contains annual data on the flows of international immigrants as recorded by the countries of destination. The data presents both inflows and outflows according to the place of birth, citizenship or place of previous / next residence both for foreigners and nationals. The current version presents data pertaining to 45 countries.</p>
<p>In this Project, we will focus on the Canadian immigration data.</p>
<p><img src = "https://ibm.box.com/shared/static/mb48k9fiylkd7z3a21cq38xxfy1wni2y.png" align="center" width= "900" /></p>
<p>For sake of simplicity, Canada's immigration data has been extracted and uploaded to one of IBM servers. You can fetch the data from <a href="https://ibm.box.com/shared/static/lw190pt9zpy5bd1ptyg2aw15awomz9pu.xlsx">here</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="1.2 Pandas-Basics"><em>1.2 Pandas</em> Basics<a id="4" /><a class="anchor-link" href="# 1.2 Pandas-Basics">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The first thing we'll do is import two key data analysis modules: <em>pandas</em> and <strong>Numpy</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>  <span class="c1"># useful for many scientific computing in Python</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span> <span class="c1"># primary data structure library</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's download and import our primary Canadian Immigration dataset using <em>pandas</em> <code>read_excel()</code> method. Normally, before we can do that, we would need to download a module which <em>pandas</em> requires to read in excel files. This module is <strong>xlrd</strong>. For your convenience, we have pre-installed this module, so you would not have to worry about that. Otherwise, you would need to run the following line of code to install the <strong>xlrd</strong> module:</p>

<pre><code>!conda install -c anaconda xlrd --yes</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now we are ready to read in our data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_excel</span><span class="p">(</span><span class="s1">&#39;https://ibm.box.com/shared/static/lw190pt9zpy5bd1ptyg2aw15awomz9pu.xlsx&#39;</span><span class="p">,</span>
                       <span class="n">sheet_name</span><span class="o">=</span><span class="s1">&#39;Canada by Citizenship&#39;</span><span class="p">,</span>
                       <span class="n">skiprows</span><span class="o">=</span><span class="nb">range</span><span class="p">(</span><span class="mi">20</span><span class="p">),</span>
                       <span class="n">skip_footer</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>

<span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;Data read into a pandas dataframe!&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's view the top 5 rows of the dataset using the <code>head()</code> function.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
<span class="c1"># tip: You can specify the number of rows you&#39;d like to see as follows: df_can.head(10) </span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can also veiw the bottom 5 rows of the dataset using the <code>tail()</code> function.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">tail</span><span class="p">()</span>
</pre></div>

    
   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>When analyzing a dataset, it's always a good idea to start by getting basic information about your dataframe. We can do this by using the <code>info()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">info</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To get the list of column headers we can call upon the dataframe's <code>.columns</code> parameter.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">values</span> 
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Similarly, to get the list of indicies we use the <code>.index</code> parameter.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Note: The default type of index and columns is NOT list.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">columns</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">index</span><span class="p">))</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To get the index and columns as lists, we can use the <code>tolist()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span>

<span class="nb">print</span> <span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">tolist</span><span class="p">()))</span>
<span class="nb">print</span> <span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">tolist</span><span class="p">()))</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To view the dimensions of the dataframe, we use the <code>.shape</code> parameter.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># size of dataframe (rows, columns)</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">shape</span>    
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Note: The main types stored in <em>pandas</em> objects are <em>float</em>, <em>int</em>, <em>bool</em>, <em>datetime64[ns]</em> and <em>datetime64[ns, tz] (in &gt;= 0.17.0)</em>, <em>timedelta[ns]</em>, <em>category (in &gt;= 0.15.0)</em>, and <em>object</em> (string). In addition these dtypes have item sizes, e.g. int64 and int32.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's clean the data set to remove a few unnecessary columns. We can use <em>pandas</em> <code>drop()</code> method as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># in pandas axis=0 represents rows (default) and axis=1 represents columns.</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;AREA&#39;</span><span class="p">,</span><span class="s1">&#39;REG&#39;</span><span class="p">,</span><span class="s1">&#39;DEV&#39;</span><span class="p">,</span><span class="s1">&#39;Type&#39;</span><span class="p">,</span><span class="s1">&#39;Coverage&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's rename the columns so that they make sense. We can use <code>rename()</code> method by passing in a dictionary of old and new names as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;OdName&#39;</span><span class="p">:</span><span class="s1">&#39;Country&#39;</span><span class="p">,</span> <span class="s1">&#39;AreaName&#39;</span><span class="p">:</span><span class="s1">&#39;Continent&#39;</span><span class="p">,</span> <span class="s1">&#39;RegName&#39;</span><span class="p">:</span><span class="s1">&#39;Region&#39;</span><span class="p">},</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">columns</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We will also add a 'Total' column that sums up the total immigrants by country over the entire period 1980 - 2013, as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can check to see how many null objects we have in the dataset as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Finally, let's view a quick summary of each column in our dataframe using the <code>describe()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<hr>
<h2 id="1.3 Pandas-Intermediate:-Indexing-and-Selection-(slicing)"><em>1.3 Pandas</em> Intermediate: Indexing and Selection (slicing)<a id="6" /><a class="anchor-link" href="#1.3 Pandas-Intermediate:-Indexing-and-Selection-(slicing)">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Select-Column">Select Column<a class="anchor-link" href="#Select-Column">&#182;</a></h3><p><strong>There are two ways to filter on a column name:</strong></p>
<p>Method 1: Quick and easy, but only works if the column name does NOT have spaces or special characters.</p>
<div class="highlight"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">column_name</span> 
        <span class="p">(</span><span class="n">returns</span> <span class="n">series</span><span class="p">)</span>
</pre></div>
<p>Method 2: More robust, and can filter on multiple columns.</p>
<div class="highlight"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;column&#39;</span><span class="p">]</span>  
        <span class="p">(</span><span class="n">returns</span> <span class="n">series</span><span class="p">)</span>
</pre></div>
<div class="highlight"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;column 1&#39;</span><span class="p">,</span> <span class="s1">&#39;column 2&#39;</span><span class="p">]]</span> 
        <span class="p">(</span><span class="n">returns</span> <span class="n">dataframe</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Example: Let's try filtering on the list of countries ('Country').</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">Country</span>  <span class="c1"># returns a series</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's try filtering on the list of countries ('OdName') and the data for years: 1980 - 1985.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="p">[[</span><span class="s1">&#39;Country&#39;</span><span class="p">,</span> <span class="mi">1980</span><span class="p">,</span> <span class="mi">1981</span><span class="p">,</span> <span class="mi">1982</span><span class="p">,</span> <span class="mi">1983</span><span class="p">,</span> <span class="mi">1984</span><span class="p">,</span> <span class="mi">1985</span><span class="p">]]</span> <span class="c1"># returns a dataframe</span>
<span class="c1"># notice that &#39;Country&#39; is string, and the years are integers. </span>
<span class="c1"># for the sake of consistency, we will convert all column names to string later on.</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Select-Row">Select Row<a class="anchor-link" href="#Select-Row">&#182;</a></h3><p>There are main 3 ways to select rows:</p>
<div class="highlight"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">label</span><span class="p">]</span>        
        <span class="c1">#filters by the labels of the index/column</span>
    <span class="n">df</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="n">index</span><span class="p">]</span>       
        <span class="c1">#filters by the positions of the index/column</span>
</pre></div>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Before we proceed, notice that the defaul index of the dataset is a numeric range from 0 to 194. This makes it very difficult to do a query by a specific country. For example to search for data on Japan, we need to know the corressponding index value.</p>
<p>This can be fixed very easily by setting the 'Country' column as the index using <code>set_index()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">set_index</span><span class="p">(</span><span class="s1">&#39;Country&#39;</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="c1"># tip: The opposite of set is reset. So to reset the index, we can use df_can.reset_index()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># optional: to remove the name of the index</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="kc">None</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Example: Let's view the number of immigrants from Japan (row 87) for the following scenarios:</p>

<pre><code>1. The full row data (all columns)
2. For year 2013
3. For years 1980 to 1985</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># 1. the full row data (all columns)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="s1">&#39;Japan&#39;</span><span class="p">])</span>

<span class="c1"># alternate methods</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">87</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="p">[</span><span class="n">df_can</span><span class="o">.</span><span class="n">index</span> <span class="o">==</span> <span class="s1">&#39;Japan&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">squeeze</span><span class="p">())</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># 2. for year 2013</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="s1">&#39;Japan&#39;</span><span class="p">,</span> <span class="mi">2013</span><span class="p">])</span>

<span class="c1"># alternate method</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">87</span><span class="p">,</span> <span class="mi">36</span><span class="p">])</span> <span class="c1"># year 2013 is the last column, with a positional index of 36</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># 3. for years 1980 to 1985</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="s1">&#39;Japan&#39;</span><span class="p">,</span> <span class="p">[</span><span class="mi">1980</span><span class="p">,</span> <span class="mi">1981</span><span class="p">,</span> <span class="mi">1982</span><span class="p">,</span> <span class="mi">1983</span><span class="p">,</span> <span class="mi">1984</span><span class="p">,</span> <span class="mi">1984</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">87</span><span class="p">,</span> <span class="p">[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="mi">7</span><span class="p">,</span> <span class="mi">8</span><span class="p">]])</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Column names that are integers (such as the years) might introduce some confusion. For example, when we are referencing the year 2013, one might confuse that when the 2013th positional index.</p>
<p>To avoid this ambuigity, let's convert the column names into strings: '1980' to '2013'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="nb">str</span><span class="p">,</span> <span class="n">df_can</span><span class="o">.</span><span class="n">columns</span><span class="p">))</span>
<span class="c1"># [print (type(x)) for x in df_can.columns.values] #&lt;-- uncomment to check type of column headers</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Since we converted the years to string, let's declare a variable that will allow us to easily call upon the full range of years:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># useful for plotting later on</span>
<span class="n">years</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="nb">str</span><span class="p">,</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1980</span><span class="p">,</span> <span class="mi">2014</span><span class="p">)))</span>
<span class="n">years</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Filtering-based-on-a-criteria">Filtering based on a criteria<a class="anchor-link" href="#Filtering-based-on-a-criteria">&#182;</a></h3><p>To filter the dataframe based on a condition, we simply pass the condition as a boolean vector.</p>
<p>For example, Let's filter the dataframe to show the data on Asian countries (AreaName = Asia).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># 1. create the condition boolean series</span>
<span class="n">condition</span> <span class="o">=</span> <span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Continent&#39;</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Asia&#39;</span>
<span class="nb">print</span> <span class="p">(</span><span class="n">condition</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># 2. pass this condition into the dataFrame</span>
<span class="n">df_can</span><span class="p">[</span><span class="n">condition</span><span class="p">]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># we can pass mutliple criteria in the same line. </span>
<span class="c1"># let&#39;s filter for AreaNAme = Asia and RegName = Southern Asia</span>

<span class="n">df_can</span><span class="p">[(</span><span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Continent&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;Asia&#39;</span><span class="p">)</span> <span class="o">&amp;</span> <span class="p">(</span><span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Region&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;Southern Asia&#39;</span><span class="p">)]</span>

<span class="c1"># note: When using &#39;and&#39; and &#39;or&#39; operators, pandas requires we use &#39;&amp;&#39; and &#39;|&#39; instead of &#39;and&#39; and &#39;or&#39;</span>
<span class="c1"># don&#39;t forget to enclose the two conditions in parentheses</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Before we proceed: let's review the changes we have made to our dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;data dimensions:&#39;</span><span class="p">,</span> <span class="n">df_can</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">columns</span><span class="p">)</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<hr>
<h1 id="2. Visualizing-Data-using-Matplotlib">2. Visualizing Data using Matplotlib<a id="8" /><a class="anchor-link" href="#2. Visualizing-Data-using-Matplotlib">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.1 Matplotlib:-Standard-Python-Visualization-Library">2.1 Matplotlib: Standard Python Visualization Library<a id="10" /><a class="anchor-link" href="#2.1 Matplotlib:-Standard-Python-Visualization-Library">&#182;</a></h2><p>The primary plotting library we will explore in the course is <a href="http://matplotlib.org/">Matplotlib</a>.  As mentioned on their website:</p>
<blockquote><p>Matplotlib is a Python 2D plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments across platforms. Matplotlib can be used in Python scripts, the Python and IPython shell, the jupyter notebook, web application servers, and four graphical user interface toolkits.</p>
</blockquote>
<p>If you are aspiring to create impactful visualization with python, Matplotlib is an essential tool to have at your disposal.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Matplotlib.Pyplot">Matplotlib.Pyplot<a class="anchor-link" href="#Matplotlib.Pyplot">&#182;</a></h3><p>One of the core aspects of Matplotlib is <code>matplotlib.pyplot</code>. It is Matplotlib's scripting layer which we studied in details in the videos about Matplotlib. Recall that it is a collection of command style functions that make Matplotlib work like MATLAB. Each <code>pyplot</code> function makes some change to a figure: e.g., creates a figure, creates a plotting area in a figure, plots some lines in a plotting area, decorates the plot with labels, etc. In this lab, we will work with the scripting layer to learn how to generate line plots. In future labs, we will get to work with the Artist layer as well to experiment first hand how it differs from the scripting layer.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's start by importing <code>Matplotlib</code> and <code>Matplotlib.pyplot</code> as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># we are using the inline backend</span>
<span class="o">%</span><span class="k">matplotlib</span> inline 

<span class="kn">import</span> <span class="nn">matplotlib</span> <span class="k">as</span> <span class="nn">mpl</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>*optional: check if Matplotlib is loaded.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;Matplotlib version: &#39;</span><span class="p">,</span> <span class="n">mpl</span><span class="o">.</span><span class="n">__version__</span><span class="p">)</span> <span class="c1"># &gt;= 2.0.0</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>*optional: apply a style to Matplotlib.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="n">plt</span><span class="o">.</span><span class="n">style</span><span class="o">.</span><span class="n">available</span><span class="p">)</span>
<span class="n">mpl</span><span class="o">.</span><span class="n">style</span><span class="o">.</span><span class="n">use</span><span class="p">([</span><span class="s1">&#39;ggplot&#39;</span><span class="p">])</span> <span class="c1"># optional: for ggplot-like style</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Plotting-in-Pandas">Plotting in <em>Pandas</em><a class="anchor-link" href="#Plotting-in-Pandas">&#182;</a></h3><p>Fortunately, pandas has a built-in implementation of Matplotlib that we can use. Plotting in <em>Pandas</em> is as simple as appending a <code>.plot()</code> method to a series or dataframe.</p>
<p>Documentation:</p>
<ul>
<li><a href="http://pandas.pydata.org/pandas-docs/stable/api.html#plotting">Plotting with Series</a><br></li>
<li><a href="http://pandas.pydata.org/pandas-docs/stable/api.html#api-dataframe-plotting">Plotting with Dataframes</a></li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.2 Line-Pots-(Series/Dataframe)-">2.2 Line Pots (Series/Dataframe) <a id="12" /><a class="anchor-link" href="#2.2 Line-Pots-(Series/Dataframe)-">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>What is a line plot and why use it?</strong></p>
<p>A line chart or line plot is a type of plot which displays information as a series of data points called 'markers' connected by straight line segments. It is a basic type of chart common in many fields.
Use line plot when you have a continuous data set. These are best suited for trend-based visualizations of data over a period of time.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Let's start with a case study:</strong></p>
<p>In 2010, Haiti suffered a catastrophic magnitude 7.0 earthquake. The quake caused widespread devastation and loss of life and aout three million people were affected by this natural disaster. As part of Canada's humanitarian effort, the Government of Canada stepped up its effort in accepting refugees from Haiti. We can quickly visualize this effort using a <code>Line</code> plot:</p>
<p><strong>Question:</strong> <strong>Plot a line graph of immigration from Haiti using <code>df.plot()</code></strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>First, we will extract the data series for Haiti.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">haiti</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="s1">&#39;Haiti&#39;</span><span class="p">,</span> <span class="n">years</span><span class="p">]</span> <span class="c1"># passing in years 1980 - 2013 to exclude the &#39;total&#39; column</span>
<span class="n">haiti</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Next, we will plot a line plot by appending <code>.plot()</code> to the <code>haiti</code> dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">haiti</span><span class="o">.</span><span class="n">plot</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><em>pandas</em> automatically populated the x-axis with the index values (years), and the y-axis with the column values (population). However, notice how the years were not displayed because they are of type <em>string</em>. Therefore, let's change the type of the index values to <em>integer</em> for plotting.</p>
<p>Also, let's label the x and y axis using <code>plt.title()</code>, <code>plt.ylabel()</code>, and <code>plt.xlabel()</code> as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">haiti</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">haiti</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span> <span class="c1"># let&#39;s change the index values of Haiti to type integer for plotting</span>
<span class="n">haiti</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;line&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration from Haiti&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span> <span class="c1"># need this line to show the updates made to the figure</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can clearly notice how number of immigrants from Haiti spiked up from 2010 as Canada stepped up its efforts to accept refugees from Haiti. Let's annotate this spike in the plot by using the <code>plt.text()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">haiti</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;line&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration from Haiti&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>

<span class="c1"># annotate the 2010 Earthquake. </span>
<span class="c1"># syntax: plt.text(x, y, label)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">text</span><span class="p">(</span><span class="mi">2000</span><span class="p">,</span> <span class="mi">6000</span><span class="p">,</span> <span class="s1">&#39;2010 Earthquake&#39;</span><span class="p">)</span> <span class="c1"># see note below</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span> 
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>With just a few lines of code, you were able to quickly identify and visualize the spike in immigration!</p>
<p>Quick note on x and y values in <code>plt.text(x, y, label)</code>:</p>

<pre><code> Since the x-axis (years) is type 'integer', we specified x as a year. The y axis (number of immigrants) is type 'integer', so we can just specify the value y = 6000.

</code></pre>
<div class="highlight"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">text</span><span class="p">(</span><span class="mi">2000</span><span class="p">,</span> <span class="mi">6000</span><span class="p">,</span> <span class="s1">&#39;2010 Earthquake&#39;</span><span class="p">)</span> <span class="c1"># years stored as type int</span>
</pre></div>

<pre><code>If the years were stored as type 'string', we would need to specify x as the index position of the year. Eg 20th index is year 2000 since it is the 20th year with a base year of 1980.
</code></pre>
<div class="highlight"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">text</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">6000</span><span class="p">,</span> <span class="s1">&#39;2010 Earthquake&#39;</span><span class="p">)</span> <span class="c1"># years stored as type int</span>
</pre></div>

<pre><code>We will cover advanced annotation methods in later modules.</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can easily add more countries to line plot to make meaningful comparisons immigration from different countries.</p>
<p><strong>Question:</strong> <strong>Let's compare the number of immigrants from India and China from 1980 to 2013.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the data set for China and India, and display dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer = </span>
<span class="n">df_CI</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;India&#39;</span><span class="p">,</span> <span class="s1">&#39;China&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Plot graph. We will explicitly specify line plot by passing in <code>kind</code> parameter to <code>plot()</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;line&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>That doesn't look right...</p>
<p>Recall that <em>pandas</em> plots the indices on the x-axis and the columns as individual lines on the y-axis. Since <code>df_CI</code> is a dataframe with the <code>country</code> as the index and <code>years</code> as the columns, we must first transpose the dataframe using <code>transpose()</code> method to swap the row and columns.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_CI</span> <span class="o">=</span> <span class="n">df_CI</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><em>pandas</em> will auomatically graph the two countries on the same graph. Go ahead and plot the new transposed dataframe. Make sure to add a title to the plot and label the axes.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">df_CI</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span> <span class="c1"># let&#39;s change the index values of df_CI to type integer for plotting</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;line&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>From the above plot, we can observe that the China and India have very similar immigration trends through the years.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><em>Note</em>: How come we didn't need to transpose Haiti's dataframe before plotting (like we did for df_CI)?</p>
<p>That's because <code>haiti</code> is a series as opposed to a dataframe, and has the years as its indices as shown below.</p>
<div class="highlight"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">haiti</span><span class="p">))</span>
<span class="k">print</span><span class="p">(</span><span class="n">haiti</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">5</span><span class="p">))</span>
</pre></div>
<blockquote><p>class 'pandas.core.series.Series' <br>
1980    1666 <br>
1981    3692 <br>
1982    3498 <br>
1983    2860 <br>
1984    1418 <br>
Name: Haiti, dtype: int64 <br></p>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Line plot is a handy tool to display several dependent variables against one independent variable. However, it is recommended that no more than 5-10 lines on a single graph; any more than that and it becomes difficult to interpret.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question:</strong> <strong>Compare the trend of top 5 countries that contributed the most to immigration to Canada.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># Step 1: Get the dataset. Recall that we created a Total column that calculates the cumulative immigration by country. \\ We will sort on this column to get our top 5 countries using pandas sort_values() method.</span>
<span class="c1"># inplace = True paramemter saves the changes to the original df_can dataframe</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">by</span><span class="o">=</span><span class="s1">&#39;Total&#39;</span><span class="p">,</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># get the top 5 entries</span>
<span class="n">df_top5</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>

<span class="c1"># transpose the dataframe</span>
<span class="n">df_top5</span> <span class="o">=</span> <span class="n">df_top5</span><span class="p">[</span><span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> 

<span class="nb">print</span><span class="p">(</span><span class="n">df_top5</span><span class="p">)</span>

<span class="c1"># Step 2: Plot the dataframe. To make the plot more readeable, we will change the size using the `figsize` parameter.</span>
<span class="n">df_top5</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">df_top5</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span> <span class="c1"># let&#39;s change the index values of df_top5 to type integer for plotting</span>
<span class="n">df_top5</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;line&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">14</span><span class="p">,</span> <span class="mi">8</span><span class="p">))</span> <span class="c1"># pass a tuple (x, y) size</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration Trend of Top 5 Countries&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>


<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.3 Pie-Charts-">2.3 Pie Charts <a id="6" /><a class="anchor-link" href="#2.3 Pie-Charts-">&#182;</a></h2><p>A <code>2.3 pie chart</code> is a circualr graphic that displays numeric proportions by dividing a circle (or pie) into proportional slices. You are most likely already familiar with pie charts as it is widely used in business and media. We can create pie charts in Matplotlib by passing in the <code>kind=pie</code> keyword.</p>
<p>Let's use a pie chart to explore the proportion (percentage) of new immigrants grouped by continents for the entire time period from 1980 to 2013.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Gather data.</p>
<p>We will use <em>pandas</em> <code>groupby</code> method to summarize the immigration data by <code>Continent</code>. The general process of <code>groupby</code> involves the following steps:</p>
<ol>
<li><strong>Split:</strong> Splitting the data into groups based on some criteria.</li>
<li><strong>Apply:</strong> Applying a function to each group independently:
<pre><code>.sum()
.count()
.mean() 
.std() 
.aggregate()
.apply()
.etc..</code></pre>
</li>
<li><strong>Combine:</strong> Combining the results into a data structure.</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/tkfhxqkehfzpclco8f0eazhie33uxj9j.png" height=400 align="center"></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># group countries by continents and apply sum() function </span>
<span class="n">df_continents</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;Continent&#39;</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>

<span class="c1"># note: the output of the groupby method is a `groupby&#39; object. </span>
<span class="c1"># we can not use it further until we apply a function (eg .sum())</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;Continent&#39;</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)))</span>

<span class="n">df_continents</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Plot the data. We will pass in <code>kind = 'pie'</code> keyword, along with the following additional parameters:</p>
<ul>
<li><code>autopct</code> -  is a string or function used to label the wedges with their numeric value. The label will be placed inside the wedge. If it is a format string, the label will be <code>fmt%pct</code>.</li>
<li><code>startangle</code> - rotates the start of the pie chart by angle degrees counterclockwise from the x-axis.</li>
<li><code>shadow</code> - Draws a shadow beneath the pie (to give a 3D feel).</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># autopct create %, start angle represent starting point</span>
<span class="n">df_continents</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;pie&#39;</span><span class="p">,</span>
                            <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">5</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span>
                            <span class="n">autopct</span><span class="o">=</span><span class="s1">&#39;</span><span class="si">%1.1f%%</span><span class="s1">&#39;</span><span class="p">,</span> <span class="c1"># add in percentages</span>
                            <span class="n">startangle</span><span class="o">=</span><span class="mi">90</span><span class="p">,</span>     <span class="c1"># start angle 90° (Africa)</span>
                            <span class="n">shadow</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>       <span class="c1"># add shadow      </span>
                            <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration to Canada by Continent [1980 - 2013]&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;equal&#39;</span><span class="p">)</span> <span class="c1"># Sets the pie chart to look like a circle.</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The above visual is not very clear, the numbers and text overlap in some instances. Let's make a few modifications to improve the visuals:</p>
<ul>
<li>Remove the text labels on the pie chart by passing in <code>legend</code> and add it as a seperate legend using <code>plt.legend()</code>.</li>
<li>Push out the percentages to sit just outside the pie chart by passing in <code>pctdistance</code> parameter.</li>
<li>Pass in a custom set of colors for continents by passing in <code>colors</code> parameter.</li>
<li><strong>Explode</strong> the pie chart to emphasize the lowest three continents (Africa, North America, and Latin America and Carribbean) by pasing in <code>explode</code> parameter.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">colors_list</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;gold&#39;</span><span class="p">,</span> <span class="s1">&#39;yellowgreen&#39;</span><span class="p">,</span> <span class="s1">&#39;lightcoral&#39;</span><span class="p">,</span> <span class="s1">&#39;lightskyblue&#39;</span><span class="p">,</span> <span class="s1">&#39;lightgreen&#39;</span><span class="p">,</span> <span class="s1">&#39;pink&#39;</span><span class="p">]</span>
<span class="n">explode_list</span> <span class="o">=</span> <span class="p">[</span><span class="mf">0.1</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">]</span> <span class="c1"># ratio for each continent with which to offset each wedge.</span>

<span class="n">df_continents</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;pie&#39;</span><span class="p">,</span>
                            <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span>
                            <span class="n">autopct</span><span class="o">=</span><span class="s1">&#39;</span><span class="si">%1.1f%%</span><span class="s1">&#39;</span><span class="p">,</span> 
                            <span class="n">startangle</span><span class="o">=</span><span class="mi">90</span><span class="p">,</span>    
                            <span class="n">shadow</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>       
                            <span class="n">labels</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span>         <span class="c1"># turn off labels on pie chart</span>
                            <span class="n">pctdistance</span><span class="o">=</span><span class="mf">1.12</span><span class="p">,</span>    <span class="c1"># the ratio between the center of each pie slice and the start of the text generated by autopct </span>
                            <span class="n">colors</span><span class="o">=</span><span class="n">colors_list</span><span class="p">,</span>  <span class="c1"># add custom colors</span>
                            <span class="n">explode</span><span class="o">=</span><span class="n">explode_list</span> <span class="c1"># &#39;explode&#39; lowest 3 continents</span>
                            <span class="p">)</span>

<span class="c1"># scale the title up by 12% to match pctdistance</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration to Canada by Continent [1980 - 2013]&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="mf">1.12</span><span class="p">)</span> 

<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;equal&#39;</span><span class="p">)</span> 

<span class="c1"># add legend</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">labels</span><span class="o">=</span><span class="n">df_continents</span><span class="o">.</span><span class="n">index</span><span class="p">,</span> <span class="n">loc</span><span class="o">=</span><span class="s1">&#39;upper left&#39;</span><span class="p">)</span> 

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question:</strong> <strong>Using a pie chart, explore the proportion (percentage) of new immigrants grouped by continents in the year 2013.</strong></p>
<p><strong>Note</strong>: You might need to play with the explore values in order to fix any overlapping slice values.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>
<span class="n">explode_list</span> <span class="o">=</span> <span class="p">[</span><span class="mf">0.1</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">,</span> <span class="mf">0.2</span><span class="p">]</span> <span class="c1"># ratio for each continent with which to offset each wedge.</span>

<span class="n">df_continents</span><span class="p">[</span><span class="s1">&#39;2013&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;pie&#39;</span><span class="p">,</span>
                            <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span>
                            <span class="n">autopct</span><span class="o">=</span><span class="s1">&#39;</span><span class="si">%1.1f%%</span><span class="s1">&#39;</span><span class="p">,</span> 
                            <span class="n">startangle</span><span class="o">=</span><span class="mi">90</span><span class="p">,</span>    
                            <span class="n">shadow</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>       
                            <span class="n">labels</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span>                 <span class="c1"># turn off labels on pie chart</span>
                            <span class="n">pctdistance</span><span class="o">=</span><span class="mf">1.12</span><span class="p">,</span>            <span class="c1"># the ratio between the pie center and start of text label</span>
                            <span class="n">explode</span><span class="o">=</span><span class="n">explode_list</span>         <span class="c1"># &#39;explode&#39; lowest 3 continents</span>
                            <span class="p">)</span>


<span class="c1"># scale the title up by 12% to match pctdistance</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration to Canada by Continent in 2013&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="mf">1.12</span><span class="p">)</span> 
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;equal&#39;</span><span class="p">)</span> 

<span class="c1"># add legend</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">labels</span><span class="o">=</span><span class="n">df_continents</span><span class="o">.</span><span class="n">index</span><span class="p">,</span> <span class="n">loc</span><span class="o">=</span><span class="s1">&#39;upper left&#39;</span><span class="p">)</span> 

<span class="c1"># show plot</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.4 Box-Plots-">2.4 Box Plots <a id="8" /><a class="anchor-link" href="#2.4 Box-Plots-">&#182;</a></h2><p>A <code>2.4 box plot</code> is a way of statistically representing the <em>distribution</em> of the data through five main dimensions:</p>
<ul>
<li><strong>Minimun:</strong> Smallest number in the dataset.</li>
<li><strong>First quartile:</strong> Middle number between the <code>minimum</code> and the <code>median</code>.</li>
<li><strong>Second quartile (Median):</strong> Middle number of the (sorted) dataset.</li>
<li><strong>Third quartile:</strong> Middle number between <code>median</code> and <code>maximum</code>.</li>
<li><strong>Maximum:</strong> Highest number in the dataset.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/9nkxsfihu8mgt1go2kfasf61sywlu123.png" width=440, align="center"></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To make a <code>box plot</code>, we can use <code>kind=box</code> in <code>plot</code> method invoked on a <em>pandas</em> series or dataframe.</p>
<p>Let's plot the box plot for the Japanese immigrants between 1980 - 2013.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the dataset. Even though we are extracting the data for just one country, we will obtain it as a dataframe. This will help us with calling the <code>dataframe.describe()</code> method to view the percentiles.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># to get a dataframe, place extra square brackets around &#39;Japan&#39;.</span>
<span class="n">df_japan</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Japan&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span>
<span class="n">df_japan</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Plot by passing in <code>kind='box'</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_japan</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;box&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">8</span><span class="p">,</span> <span class="mi">6</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Box plot of Japanese Immigrants from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can immediately make a few key observations from the plot above:</p>
<ol>
<li>The minimum number of immigrants is around 200 (min), maximum number is around 1300 (max), and  median number of immigrants is around 900 (median).</li>
<li>25% of the years for period 1980 - 2013 had an annual immigrant count of ~500 or fewer (First quartile).</li>
<li>75% of the years for period 1980 - 2013 had an annual immigrant count of ~1100 or fewer (Third quartile).</li>
</ol>
<p>We can view the actual numbers by calling the <code>describe()</code> method on the dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_japan</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>One of the key benefits of box plots is comparing the distribution of multiple datasets. In one of the previous labs, we observed that China and India had very similar immigration trends. Let's analyize these two countries further using box plots.</p>
<p><strong>Question:</strong> <strong>Compare the distribution of the number of new immigrants from India and China for the period 1980 - 2013.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the dataset for China and India and call the dataframe <strong>df_CI</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="n">df_CI</span><span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;China&#39;</span><span class="p">,</span> <span class="s1">&#39;India&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's view the percentages associated with both countries using the <code>describe()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="n">df_CI</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Plot data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="n">df_CI</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;box&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">7</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Box plots of Immigrants from China and India (1980 - 2013)&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can observe that, while both countries have around the same median immigrant population (~20,000),  China's immigrant population range is more spread out than India's. The maximum population from India for any year (36,210) is around 15% lower than the maximum population from China (42,584).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>If you prefer to create horizontal box plots, you can pass the <code>vert</code> parameter in the <strong>plot</strong> function and assign it to <em>False</em>. You can also specify a different color in case you are not a big fan of the default red color.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># horizontal box plots</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;box&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">7</span><span class="p">),</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span> <span class="n">vert</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Box plots of Immigrants from China and India (1980 - 2013)&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Subplots</strong></p>
<p>Often times we might want to plot multiple plots within the same figure. For example, we might want to perform a side by side comparison of the box plot with the line plot of China and India's immigration.</p>
<p>To visualize multiple plots together, we can create a <strong><code>figure</code></strong> (overall canvas) and divide it into <strong><code>subplots</code></strong>, each containing a plot. With <strong>subplots</strong>, we usually work with the <strong>artist layer</strong> instead of the <strong>scripting layer</strong>.</p>
<p>Typical syntax is : <br></p>
<div class="highlight"><pre><span></span><span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span> <span class="c1"># create figure</span>
    <span class="n">ax</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="n">nrows</span><span class="p">,</span> <span class="n">ncols</span><span class="p">,</span> <span class="n">plot_number</span><span class="p">)</span> <span class="c1"># create subplots</span>
</pre></div>
<p>Where</p>
<ul>
<li><code>nrows</code> and <code>ncols</code> are used to notionally split the figure into (<code>nrows</code> * <code>ncols</code>) sub-axes,  </li>
<li><code>plot_number</code> is used to identify the particular subplot that this function is to create within the notional grid. <code>plot_number</code> starts at 1, increments across rows first and has a maximum of <code>nrows</code> * <code>ncols</code> as shown below.</li>
</ul>
<p><img src="https://ibm.box.com/shared/static/03rhrfcealyoi83tigscovgglfchfyor.png" width=500 align="center"></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can then specify which subplot to place each plot by passing in the <code>ax</code> paramemter in <code>plot()</code> method as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span> <span class="c1"># create figure</span>

<span class="n">ax0</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span> <span class="c1"># add subplot 1 (1 row, 2 columns, first plot)</span>
<span class="n">ax1</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span> <span class="c1"># add subplot 2 (1 row, 2 columns, second plot). See tip below**</span>

<span class="c1"># Subplot 1: Box plot</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;box&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span> <span class="n">vert</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax0</span><span class="p">)</span> <span class="c1"># add to subplot 1</span>
<span class="n">ax0</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Box Plots of Immigrants from China and India (1980 - 2013)&#39;</span><span class="p">)</span>
<span class="n">ax0</span><span class="o">.</span><span class="n">set_xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">ax0</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">&#39;Countries&#39;</span><span class="p">)</span>

<span class="c1"># Subplot 2: Line plot</span>
<span class="n">df_CI</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;line&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax1</span><span class="p">)</span> <span class="c1"># add to subplot 2</span>
<span class="n">ax1</span><span class="o">.</span><span class="n">set_title</span> <span class="p">(</span><span class="s1">&#39;Line Plots of Immigrants from China and India (1980 - 2013)&#39;</span><span class="p">)</span>
<span class="n">ax1</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">ax1</span><span class="o">.</span><span class="n">set_xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong> * Tip regarding subplot convention </strong></p>
<p>In the case when <code>nrows</code>, <code>ncols</code>, and <code>plot_number</code> are all less than 10, a convenience exists such that the a 3 digit number can be given instead, where the hundreds represent <code>nrows</code>, the tens represent <code>ncols</code> and the units represent <code>plot_number</code>. For instance,</p>
<div class="highlight"><pre><span></span><span class="n">subplot</span><span class="p">(</span><span class="mi">211</span><span class="p">)</span> <span class="o">==</span> <span class="n">subplot</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>
</pre></div>
<p>produces a subaxes in a figure which represents the top plot (i.e. the first) in a 2 rows by 1 column notional grid (no grid actually exists, but conceptually this is how the returned subplot has been positioned).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's try something a little more advanced.</p>
<p>Previously we identified the top 15 countries based on total immigration from 1980 - 2013.</p>
<p><strong>Question:</strong> <strong>Create a box plot to visualize the distribution of the top 15 countries (based on total immigration) grouped by the <em>decades</em> <code>1980s</code>, <code>1990s</code>, and <code>2000s</code>.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the dataset. Get the top 15 countries based on Total immigrant population. Name the dataframe <strong>df_top15</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="n">df_top15</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">sort_values</span><span class="p">([</span><span class="s1">&#39;Total&#39;</span><span class="p">],</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">15</span><span class="p">)</span>
<span class="n">df_top15</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Create a new dataframe which contains the aggregate for each decade. One way to do that:</p>
<ol>
<li>Create a list of all years in decades 80's, 90's, and 00's.</li>
<li>Slice the original dataframe df_can to create a series for each decade and sum across all years for each country.</li>
<li>Merge the three series into a new data frame. Call your dataframe <strong>new_df</strong>.</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># create a list of all years in decades 80&#39;s, 90&#39;s, and 00&#39;s</span>
<span class="n">years_80s</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="nb">str</span><span class="p">,</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1980</span><span class="p">,</span> <span class="mi">1990</span><span class="p">)))</span> 
<span class="n">years_90s</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="nb">str</span><span class="p">,</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1990</span><span class="p">,</span> <span class="mi">2000</span><span class="p">)))</span> 
<span class="n">years_00s</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="nb">str</span><span class="p">,</span> <span class="nb">range</span><span class="p">(</span><span class="mi">2000</span><span class="p">,</span> <span class="mi">2010</span><span class="p">)))</span> 

<span class="c1"># slice the original dataframe df_can to create a series for each decade</span>
<span class="n">df_80s</span> <span class="o">=</span> <span class="n">df_top15</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span> <span class="n">years_80s</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span> 
<span class="n">df_90s</span> <span class="o">=</span> <span class="n">df_top15</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span> <span class="n">years_90s</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span> 
<span class="n">df_00s</span> <span class="o">=</span> <span class="n">df_top15</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span> <span class="n">years_00s</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="c1"># merge the three series into a new data frame</span>
<span class="n">new_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">({</span><span class="s1">&#39;1980s&#39;</span><span class="p">:</span> <span class="n">df_80s</span><span class="p">,</span> <span class="s1">&#39;1990s&#39;</span><span class="p">:</span> <span class="n">df_90s</span><span class="p">,</span> <span class="s1">&#39;2000s&#39;</span><span class="p">:</span><span class="n">df_00s</span><span class="p">})</span> 

<span class="c1"># display dataframe</span>
<span class="n">new_df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's learn more about the statistics associated with the dataframe using the <code>describe()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="n">new_df</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 3: Plot the box plots.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### type your answer here</span>

<span class="n">new_df</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;box&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration from top 15 countries for decades 80s, 90s and 2000s&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Note how the box plot differs from the summary table created. The box plot scans the data and identifies the outliers. In order to be an outlier, the data value must be:<br></p>
<ul>
<li>larger than Q3 by at least 1.5 times the interquartile range (IQR), or,</li>
<li>smaller than Q1 by at least 1.5 times the IQR.</li>
</ul>
<p>Let's look at decade 2000s as an example: <br></p>
<ul>
<li>Q1 (25%) = 36,101.5 <br></li>
<li>Q3 (75%) = 105,505.5 <br></li>
<li>IQR = Q3 - Q1 = 69,404 <br></li>
</ul>
<p>Using the definition of outlier, any value that is greater than Q3 by 1.5 times IQR will be flagged as outlier.</p>
<p>Outlier &gt; 105,505.5 + (1.5 * 69,404) <br>
Outlier &gt; 209,611.5</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># let&#39;s check how many entries fall above the outlier threshold </span>
<span class="n">new_df</span><span class="p">[</span><span class="n">new_df</span><span class="p">[</span><span class="s1">&#39;2000s&#39;</span><span class="p">]</span><span class="o">&gt;</span> <span class="mf">209611.5</span><span class="p">]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>China and India are both considered as outliers since their population for the decade exceeds 209,611.5.</p>
<p>The box plot is an advanced visualizaiton tool, and there are many options and customizations that exceed the scope of this lab. Please refer to <a href="http://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.boxplot">Matplotlib documentation</a> on box plots for more information.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.5 Scatter-Plots-">2.5 Scatter Plots <a id="10" /><a class="anchor-link" href="#2.5 Scatter-Plots-">&#182;</a></h2><p>A <code>2.5 scatter plot</code> (2D) is a useful method of comparing variables against each other. <code>Scatter</code> plots look similar to <code>line plots</code> in that they both map independent and dependent variables on a 2D graph. While the datapoints are connected together by a line in a line plot, they are not connected in a scatter plot. The data in a scatter plot is considered to express a trend. With further analysis using tools like regression, we can mathematically calculate this relationship and use it to predict trends outside the dataset.</p>
<p>Let's start by exploring the following:</p>
<p>Using a <code>scatter plot</code>, let's visualize the trend of total immigrantion to Canada (all countries combined) for the years 1980 - 2013.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the dataset. Since we are expecting to use the relationship betewen <code>years</code> and <code>total population</code>, we will convert <code>years</code> to <code>int</code> type.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># we can use the sum() method to get the total population per year</span>
<span class="n">df_tot</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">df_can</span><span class="p">[</span><span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span>

<span class="c1"># change the years to type int (useful for regression later on)</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="nb">map</span><span class="p">(</span><span class="nb">int</span><span class="p">,</span> <span class="n">df_tot</span><span class="o">.</span><span class="n">index</span><span class="p">)</span>

<span class="c1"># reset the index to put in back in as a column in the df_tot dataframe</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>

<span class="c1"># rename columns</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="s1">&#39;total&#39;</span><span class="p">]</span>

<span class="c1"># view the final dataframe</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Plot the data. In <code>Matplotlib</code>, we can create a <code>scatter</code> plot set by passing in <code>kind='scatter'</code> as plot argument. We will also need to pass in <code>x</code> and <code>y</code> keywords to specify the columns that go on the x- and the y-axis.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_tot</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;scatter&#39;</span><span class="p">,</span> <span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;darkblue&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Total Immigration to Canada from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Year&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Notice how the scatter plot does not connect the datapoints together. We can clearly observe an upward trend in the data: as the years go by, the total number of immigrants increases. We can mathematically analyze this upward trend using a regression line (line of best fit).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>So let's try to plot a linear line of best fit, and use it to  predict the number of immigrants in 2015.</p>
<p>Step 1: Get the equation of line of best fit. We will use <strong>Numpy</strong>'s <code>polyfit()</code> method by passing in the following:</p>
<ul>
<li><code>x</code>: x-coordinates of the data. </li>
<li><code>y</code>: y-coordinates of the data. </li>
<li><code>deg</code>: Degree of fitting polynomial. 1 = linear, 2 = quadratic, and so on.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">df_tot</span><span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">]</span>      <span class="c1"># year on x-axis</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">df_tot</span><span class="p">[</span><span class="s1">&#39;total&#39;</span><span class="p">]</span>     <span class="c1"># total on y-axis</span>
<span class="n">fit</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">polyfit</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="n">deg</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="n">fit</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The output is an array with the polynomial coefficients, highest powers first. Since we are plotting a linear regression <code>y= a*x + b</code>, our output has 2 elements <code>[5.56709228e+03, -1.09261952e+07]</code> with the the slope in position 0 and intercept in position 1.</p>
<p>Step 2: Plot the regression line on the <code>scatter plot</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_tot</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;scatter&#39;</span><span class="p">,</span> <span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;darkblue&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Total Immigration to Canada from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Year&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="c1"># plot line of best fit</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">fit</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">*</span> <span class="n">x</span> <span class="o">+</span> <span class="n">fit</span><span class="p">[</span><span class="mi">1</span><span class="p">],</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;red&#39;</span><span class="p">)</span> <span class="c1"># recall that x is the Years</span>
<span class="n">plt</span><span class="o">.</span><span class="n">annotate</span><span class="p">(</span><span class="s1">&#39;y=</span><span class="si">{0:.0f}</span><span class="s1"> x + </span><span class="si">{1:.0f}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">fit</span><span class="p">[</span><span class="mi">0</span><span class="p">],</span> <span class="n">fit</span><span class="p">[</span><span class="mi">1</span><span class="p">]),</span> <span class="n">xy</span><span class="o">=</span><span class="p">(</span><span class="mi">2000</span><span class="p">,</span> <span class="mi">150000</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>

<span class="c1"># print out the line of best fit</span>
<span class="s1">&#39;No. Immigrants = </span><span class="si">{0:.0f}</span><span class="s1"> * Year + </span><span class="si">{1:.0f}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">fit</span><span class="p">[</span><span class="mi">0</span><span class="p">],</span> <span class="n">fit</span><span class="p">[</span><span class="mi">1</span><span class="p">])</span> 
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Using the equation of line of best fit, we can estimate the number of immigrants in 2015:</p>
<div class="highlight"><pre><span></span><span class="n">No</span><span class="o">.</span> <span class="n">Immigrants</span> <span class="o">=</span> <span class="mi">5567</span> <span class="o">*</span> <span class="n">Year</span> <span class="o">-</span> <span class="mi">10926195</span>
<span class="n">No</span><span class="o">.</span> <span class="n">Immigrants</span> <span class="o">=</span> <span class="mi">5567</span> <span class="o">*</span> <span class="mi">2015</span> <span class="o">-</span> <span class="mi">10926195</span>
<span class="n">No</span><span class="o">.</span> <span class="n">Immigrants</span> <span class="o">=</span> <span class="mi">291</span><span class="p">,</span><span class="mi">310</span>
</pre></div>
<p>When compared to the actuals from Citizenship and Immigration Canada's (CIC) <a href="http://www.cic.gc.ca/english/resources/publications/annual-report-2016/index.asp">2016 Annual Report</a>, we see that Canada accepted 271,845 immigrants in 2015. Our estimated value of 291,310 is within 7% of the actual number, which is pretty good considering our original data came from United Nations (and might differ slightly from CIC data).</p>
<p>As a side note, we can observe that immigration took a dip around 1993 - 1997. Further analysis into the topic revealed that in 1993 Canada introcuded Bill C-86 which introduced revisions to the refugee determination system, mostly restrictive. Further amendments to the Immigration Regulations cancelled the sponsorship required for "assisted relatives" and reduced the points awarded to them, making it more difficult for family members (other than nuclear family) to immigrate to Canada. These restrictive measures had a direct impact on the immigration numbers for the next several years.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: <strong>Create a scatter plot of the total immigration from Denmark, Norway, and Sweden to Canada from 1980 to 2013?</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the data:</p>
<ol>
<li>Create a dataframe the consists of the numbers associated with Denmark, Norway, and Sweden only. Name it <strong>df_countries</strong>.</li>
<li>Sum the immigration numbers across all three countries for each year and turn the result into a dataframe. Name this new dataframe <strong>df_total</strong>.</li>
<li>Reset the index in place.</li>
<li>Rename the columns to <strong>year</strong> and <strong>total</strong>.</li>
<li>Display the resulting dataframe.</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># create df_countries dataframe</span>
<span class="n">df_countries</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Denmark&#39;</span><span class="p">,</span> <span class="s1">&#39;Norway&#39;</span><span class="p">,</span> <span class="s1">&#39;Sweden&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span>

<span class="c1"># create df_total by summing across three countries for each year</span>
<span class="n">df_total</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">df_countries</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>

<span class="c1"># reset index in place</span>
<span class="n">df_total</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># rename columns</span>
<span class="n">df_total</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="s1">&#39;total&#39;</span><span class="p">]</span>

<span class="c1"># change column year from string to int to create scatter plot</span>
<span class="n">df_total</span><span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_total</span><span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span>

<span class="c1"># show resulting dataframe</span>
<span class="n">df_total</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Generate the scatter plot by plotting the total versus year in <strong>df_total</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># generate scatter plot</span>
<span class="n">df_total</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;scatter&#39;</span><span class="p">,</span> <span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;darkblue&#39;</span><span class="p">)</span>

<span class="c1"># add title and label to axes</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration from Denmark, Norway, and Sweden to Canada from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Year&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="c1"># show plot</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.6 Bubble-Plots-">2.6 Bubble Plots <a id="12" /><a class="anchor-link" href="#2.6 Bubble-Plots-">&#182;</a></h2><p>A <code>2.6 bubble plot</code> is a variation of the <code>scatter plot</code> that displays three dimensions of data (x, y, z). The datapoints are replaced with bubbles, and the size of the bubble is determined by the third variable 'z', also known as the weight. In <code>maplotlib</code>, we can pass in an array or scalar to the keyword <code>s</code> to <code>plot()</code>, that contains the weight of each point.</p>
<p><strong>Let's start by analyzing the effect of Argentina's great depression</strong>.</p>
<p>Argentina suffered a great depression from 1998 - 2002, which caused widespread unemployment, riots, the fall of the government, and a default on the country's foreign debt. In terms of income, over 50% of Argentines were poor, and seven out of ten Argentine children were poor at the depth of the crisis in 2002.</p>
<p>Let's analyze the effect of this crisis, and compare Argentina's immigration to that of it's neighbour Brazil. Let's do that using a <code>bubble plot</code> of immigration from Brazil and Argentina for the years 1980 - 2013. We will set the weights for the bubble as the <em>normalized</em> value of the population for each year.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the data for Brazil and Argentina. Like in the previous example, we will convert the <code>Years</code> to type int and bring it in the dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can_t</span> <span class="o">=</span> <span class="n">df_can</span><span class="p">[</span><span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> <span class="c1"># transposed dataframe</span>

<span class="c1"># cast the Years (the index) to type int</span>
<span class="n">df_can_t</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="nb">map</span><span class="p">(</span><span class="nb">int</span><span class="p">,</span> <span class="n">df_can_t</span><span class="o">.</span><span class="n">index</span><span class="p">)</span>

<span class="c1"># let&#39;s label the index. This will automatically be the column name when we reset the index</span>
<span class="n">df_can_t</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="s1">&#39;Year&#39;</span>

<span class="c1"># reset index to bring the Year in as a column</span>
<span class="n">df_can_t</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># view the changes</span>
<span class="n">df_can_t</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Create the normalized weights.</p>
<p>There are several methods of normalizations in statistics, each with its own use. In this case, we will use <a href="https://en.wikipedia.org/wiki/Feature_scaling">feature scaling</a> to bring all values into the range [0,1]. The general formula is:</p>
<p><img src="https://ibm.box.com/shared/static/3e43kt5j9wj4326x1lh8z2jeqzgpk3jv.png" align="center"></p>
<p>where <em><code>X</code></em> is an original value, <em><code>X'</code></em> is the normalized value. The formula sets the max value in the dataset to 1, and sets the min value to 0. The rest of the datapoints are scaled to a value between 0-1 accordingly.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># normalize Brazil data</span>
<span class="n">norm_brazil</span> <span class="o">=</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Brazil&#39;</span><span class="p">]</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Brazil&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span> <span class="o">/</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Brazil&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Brazil&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span>

<span class="c1"># normalize Argentina data</span>
<span class="n">norm_argentina</span> <span class="o">=</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Argentina&#39;</span><span class="p">]</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Argentina&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span> <span class="o">/</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Argentina&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;Argentina&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 3: Plot the data.</p>
<ul>
<li>To plot two different scatter plots in one plot, we can include the axes one plot into the other by passing it via the <code>ax</code> parameter. </li>
<li>We will also pass in the weights using the <code>s</code> parameter. Given that the normalized weights are between 0-1, they won't be visible on the plot. Therefore we will:<ul>
<li>multiply weights by 2000 to scale it up on the graph, and,</li>
<li>add 10 to compensate for the min value (which has a 0 weight and therefore scale with x2000).</li>
</ul>
</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Brazil</span>
<span class="n">ax0</span> <span class="o">=</span> <span class="n">df_can_t</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;scatter&#39;</span><span class="p">,</span>
                    <span class="n">x</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span>
                    <span class="n">y</span><span class="o">=</span><span class="s1">&#39;Brazil&#39;</span><span class="p">,</span>
                    <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">14</span><span class="p">,</span> <span class="mi">8</span><span class="p">),</span>
                    <span class="n">alpha</span><span class="o">=</span><span class="mf">0.5</span><span class="p">,</span>                  <span class="c1"># transparency</span>
                    <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span>
                    <span class="n">s</span><span class="o">=</span><span class="n">norm_brazil</span> <span class="o">*</span> <span class="mi">2000</span> <span class="o">+</span> <span class="mi">10</span><span class="p">,</span>  <span class="c1"># pass in weights </span>
                    <span class="n">xlim</span><span class="o">=</span><span class="p">(</span><span class="mi">1975</span><span class="p">,</span> <span class="mi">2015</span><span class="p">)</span>
                   <span class="p">)</span>

<span class="c1"># Argentina</span>
<span class="n">ax1</span> <span class="o">=</span> <span class="n">df_can_t</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;scatter&#39;</span><span class="p">,</span>
                    <span class="n">x</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span>
                    <span class="n">y</span><span class="o">=</span><span class="s1">&#39;Argentina&#39;</span><span class="p">,</span>
                    <span class="n">alpha</span><span class="o">=</span><span class="mf">0.5</span><span class="p">,</span>
                    <span class="n">color</span><span class="o">=</span><span class="s2">&quot;blue&quot;</span><span class="p">,</span>
                    <span class="n">s</span><span class="o">=</span><span class="n">norm_argentina</span> <span class="o">*</span> <span class="mi">2000</span> <span class="o">+</span> <span class="mi">10</span><span class="p">,</span>
                    <span class="n">ax</span> <span class="o">=</span> <span class="n">ax0</span>
                   <span class="p">)</span>

<span class="n">ax0</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">ax0</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Immigration from Brazil and Argentina from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">ax0</span><span class="o">.</span><span class="n">legend</span><span class="p">([</span><span class="s1">&#39;Brazil&#39;</span><span class="p">,</span> <span class="s1">&#39;Argentina&#39;</span><span class="p">],</span> <span class="n">loc</span><span class="o">=</span><span class="s1">&#39;upper left&#39;</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="s1">&#39;x-large&#39;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The size of the bubble corresponds to the magnitude of immigrating population for that year, compared to the 1980 - 2013 data. The larger the bubble, the more immigrants in that year.</p>
<p>From the plot above, we can see a corresponding increase in immigration from Argentina during the 1998 - 2002 great depression. We can also observe a similar spike around 1985 to 1993. In fact, Argentina had suffered a great depression from 1974 - 1990, just before the onset of 1998 - 2002 great depression.</p>
<p>On a similar note, Brazil suffered the <em>Samba Effect</em> where the Brazilian real (currency) dropped nearly 35% in 1999. There was a fear of a South American financial crisis as many South American countries were heavily dependent on industrial exports from Brazil. The Brazilian government subsequently adopted an austerity program, and the economy slowly recovered over the years, culminating in a surge in 2010. The immigration data reflect these events.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: <strong>Previously in this lab, we created box plots to compare immigration from China and India to Canada. Create bubble plots of immigration from China and India to visualize any differences with time from 1980 to 2013. You can use (df_can_t) that we defined and used in the previous example.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Normalize the data pertaining to China and India.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># normalize China data</span>
<span class="n">norm_china</span> <span class="o">=</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;China&#39;</span><span class="p">]</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;China&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span> <span class="o">/</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;China&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;China&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span>

<span class="c1"># normalize India data</span>
<span class="n">norm_india</span> <span class="o">=</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;India&#39;</span><span class="p">]</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;India&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span> <span class="o">/</span> <span class="p">(</span><span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;India&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span> <span class="o">-</span> <span class="n">df_can_t</span><span class="p">[</span><span class="s1">&#39;India&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Generate the bubble plots.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># China</span>
<span class="n">ax0</span> <span class="o">=</span> <span class="n">df_can_t</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;scatter&#39;</span><span class="p">,</span>
                    <span class="n">x</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span>
                    <span class="n">y</span><span class="o">=</span><span class="s1">&#39;China&#39;</span><span class="p">,</span>
                    <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">14</span><span class="p">,</span> <span class="mi">8</span><span class="p">),</span>
                    <span class="n">alpha</span><span class="o">=</span><span class="mf">0.5</span><span class="p">,</span>                  <span class="c1"># transparency</span>
                    <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span>
                    <span class="n">s</span><span class="o">=</span><span class="n">norm_china</span> <span class="o">*</span> <span class="mi">2000</span> <span class="o">+</span> <span class="mi">10</span><span class="p">,</span>  <span class="c1"># pass in weights </span>
                    <span class="n">xlim</span><span class="o">=</span><span class="p">(</span><span class="mi">1975</span><span class="p">,</span> <span class="mi">2015</span><span class="p">)</span>
                   <span class="p">)</span>

<span class="c1"># India</span>
<span class="n">ax1</span> <span class="o">=</span> <span class="n">df_can_t</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;scatter&#39;</span><span class="p">,</span>
                    <span class="n">x</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span>
                    <span class="n">y</span><span class="o">=</span><span class="s1">&#39;India&#39;</span><span class="p">,</span>
                    <span class="n">alpha</span><span class="o">=</span><span class="mf">0.5</span><span class="p">,</span>
                    <span class="n">color</span><span class="o">=</span><span class="s2">&quot;blue&quot;</span><span class="p">,</span>
                    <span class="n">s</span><span class="o">=</span><span class="n">norm_india</span> <span class="o">*</span> <span class="mi">2000</span> <span class="o">+</span> <span class="mi">10</span><span class="p">,</span>
                    <span class="n">ax</span> <span class="o">=</span> <span class="n">ax0</span>
                   <span class="p">)</span>

<span class="n">ax0</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">ax0</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Immigration from China and India from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">ax0</span><span class="o">.</span><span class="n">legend</span><span class="p">([</span><span class="s1">&#39;China&#39;</span><span class="p">,</span> <span class="s1">&#39;India&#39;</span><span class="p">],</span> <span class="n">loc</span><span class="o">=</span><span class="s1">&#39;upper left&#39;</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="s1">&#39;x-large&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span> 
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.7 Area-Plots">2.7 Area Plots<a id="6" /><a class="anchor-link" href="#2.7 Area-Plots">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In the last module, we created a line plot that visualized the top 5 countries that contribued the most immigrants to Canada from 1980 to 2013. With a little modification to the code, we can visualize this plot as a cumulative plot, also knows as a <strong>Stacked Line Plot</strong> or <strong>Area plot</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">sort_values</span><span class="p">([</span><span class="s1">&#39;Total&#39;</span><span class="p">],</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># get the top 5 entries</span>
<span class="n">df_top5</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>

<span class="c1"># transpose the dataframe</span>
<span class="n">df_top5</span> <span class="o">=</span> <span class="n">df_top5</span><span class="p">[</span><span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> 

<span class="n">df_top5</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Area plots are stacked by default. And to produce a stacked area plot, each column must be either all positive or all negative values (any NaN values will defaulted to 0). To produce an unstacked plot, pass <code>stacked=False</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_top5</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">df_top5</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span> <span class="c1"># let&#39;s change the index values of df_top5 to type integer for plotting</span>
<span class="n">df_top5</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;area&#39;</span><span class="p">,</span> 
             <span class="n">stacked</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span>
             <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">10</span><span class="p">),</span> <span class="c1"># pass a tuple (x, y) size</span>
             <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration Trend of Top 5 Countries&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The unstacked plot has a default transparency (alpha value) at 0.5. We can modify this value by passing in the <code>alpha</code> parameter.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_top5</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;area&#39;</span><span class="p">,</span> 
             <span class="n">alpha</span><span class="o">=</span><span class="mf">0.25</span><span class="p">,</span> <span class="c1"># 0-1, default value a= 0.5</span>
             <span class="n">stacked</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span>
             <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">10</span><span class="p">),</span>
            <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration Trend of Top 5 Countries&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Two-types-of-plotting">Two types of plotting<a class="anchor-link" href="#Two-types-of-plotting">&#182;</a></h3><p>As we discussed in the video lectures, there are two styles/options of ploting with <code>matplotlib</code>. Plotting using the Artist layer and plotting using the scripting layer.</p>
<p><strong>Option 1: Scripting layer (procedural method) - using matplotlib.pyplot as 'plt' </strong></p>
<p>You can use <code>plt</code> i.e. <code>matplotlib.pyplot</code> and add more elements by calling different methods procedurally; for example, <code>plt.title(...)</code> to add title or <code>plt.xlabel(...)</code> to add label to the x-axis.</p>
<div class="highlight"><pre><span></span><span class="c1"># Option 1: This is what we have been using so far</span>
    <span class="n">df_top5</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;area&#39;</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="mf">0.35</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span> 
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration trend of top 5 countries&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of immigrants&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Option 2: Artist layer (Object oriented method) - using an <code>Axes</code> instance from Matplotlib (preferred) </strong></p>
<p>You can use an <code>Axes</code> instance of your current plot and store it in a variable (eg. <code>ax</code>). You can add more elements by calling methods with a little change in syntax (by adding "<em>set_</em>" to the previous methods). For example, use <code>ax.set_title()</code> instead of <code>plt.title()</code> to add title,  or <code>ax.set_xlabel()</code> instead of <code>plt.xlabel()</code> to add label to the x-axis.</p>
<p>This option sometimes is more transparent and flexible to use for advanced plots (in particular when having multiple plots, as you will see later).</p>
<p>In this course, we will stick to the <strong>scripting layer</strong>, except for some advanced visualizations where we will need to use the <strong>artist layer</strong> to manipulate advanced aspects of the plots.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># option 2: preferred option with more flexibility</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">df_top5</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;area&#39;</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="mf">0.35</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>

<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Immigration Trend of Top 5 Countries&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: <strong>Use the scripting layer to create a stacked area plot of the 5 countries that contributed the least to immigration to Canada from 1980 to 2013. Use a transparency value of 0.45.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># get the 5 countries with the least contribution</span>
<span class="n">df_least5</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">tail</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>

<span class="c1"># transpose the dataframe</span>
<span class="n">df_least5</span> <span class="o">=</span> <span class="n">df_least5</span><span class="p">[</span><span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> 
<span class="n">df_least5</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>

<span class="n">df_least5</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">df_least5</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span> <span class="c1"># let&#39;s change the index values of df_least5 to type integer for plotting</span>
<span class="n">df_least5</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;area&#39;</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="mf">0.45</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span> 

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Immigration Trend of 5 Countries with Least Contribution to Immigration&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>:<strong>Use the artist layer to create an unstacked area plot of the 5 countries that contributed the least to immigration to Canada from 1980 to 2013. Use a transparency value of 0.55.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># get the 5 countries with the least contribution</span>
<span class="n">df_least5</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">tail</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>

<span class="c1"># transpose the dataframe</span>
<span class="n">df_least5</span> <span class="o">=</span> <span class="n">df_least5</span><span class="p">[</span><span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> 
<span class="n">df_least5</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>

<span class="n">df_least5</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">df_least5</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span> <span class="c1"># let&#39;s change the index values of df_least5 to type integer for plotting</span>

<span class="n">ax</span> <span class="o">=</span> <span class="n">df_least5</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;area&#39;</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="mf">0.55</span><span class="p">,</span> <span class="n">stacked</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>

<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Immigration Trend of 5 Countries with Least Contribution to Immigration&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_xlabel</span><span class="p">(</span><span class="s1">&#39;Years&#39;</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.8 Histograms">2.8 Histograms<a id="8" /><a class="anchor-link" href="#2.8 Histograms">&#182;</a></h2><p>A histogram is a way of representing the <em>frequency</em> distribution of numeric dataset. The way it works is it partitions the x-axis into <em>bins</em>, assigns each data point in our dataset to a bin, and then counts the number of data points that have been assigned to each bin. So the y-axis is the frequency or the number of data points in each bin. Note that we can change the bin size and usually one needs to tweak it so that the distribution is displayed nicely.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question:</strong> <strong>What is the frequency distribution of the number (population) of new immigrants from the various countries to Canada in 2013?</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Before we proceed with creating the histogram plot, let's first examine the data split into intervals. To do this, we will us <strong>Numpy</strong>'s <code>histrogram</code> method to get the bin ranges and frequency counts as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># let&#39;s quickly view the 2013 data</span>
<span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;2013&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># np.histogram returns 2 values</span>
<span class="n">count</span><span class="p">,</span> <span class="n">bin_edges</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">histogram</span><span class="p">(</span><span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;2013&#39;</span><span class="p">])</span>

<span class="nb">print</span><span class="p">(</span><span class="n">count</span><span class="p">)</span> <span class="c1"># frequency count</span>
<span class="nb">print</span><span class="p">(</span><span class="n">bin_edges</span><span class="p">)</span> <span class="c1"># bin ranges, default = 10 bins</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>By default, the <code>histrogram</code> method breaks up the dataset into 10 bins. The figure below summarizes the bin ranges and the frequency distribution of immigration in 2013. We can see that in 2013:</p>
<ul>
<li>178 countries contributed between 0 to 3412.9 immigrants </li>
<li>11 countries contributed between 3412.9 to 6825.8 immigrants</li>
<li>1 country contributed between 6285.8 to 10238.7 immigrants, and so on..</li>
</ul>
<p><img src="https://ibm.box.com/shared/static/g54s9q97mrjok0h4272o7g09cyigei0v.jpg" align="center" width=800></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can easily graph this distribution by passing <code>kind=hist</code> to <code>plot()</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;2013&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;hist&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">8</span><span class="p">,</span> <span class="mi">5</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Histogram of Immigration from 195 Countries in 2013&#39;</span><span class="p">)</span> <span class="c1"># add a title to the histogram</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Countries&#39;</span><span class="p">)</span> <span class="c1"># add y-label</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span> <span class="c1"># add x-label</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In the above plot, the x-axis represents the population range of immigrants in intervals of 3412.9. The y-axis represents the number of countries that contributed to the aforementioned population.</p>
<p>Notice that the x-axis labels do not match with the bin size. This can be fixed by passing in a <code>xticks</code> keyword that contains the list of the bin sizes, as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># &#39;bin_edges&#39; is a list of bin intervals</span>
<span class="n">count</span><span class="p">,</span> <span class="n">bin_edges</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">histogram</span><span class="p">(</span><span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;2013&#39;</span><span class="p">])</span>

<span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;2013&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;hist&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">8</span><span class="p">,</span> <span class="mi">5</span><span class="p">),</span> <span class="n">xticks</span><span class="o">=</span><span class="n">bin_edges</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Histogram of Immigration from 195 countries in 2013&#39;</span><span class="p">)</span> <span class="c1"># add a title to the histogram</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Countries&#39;</span><span class="p">)</span> <span class="c1"># add y-label</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span> <span class="c1"># add x-label</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><em>Side Note:</em> We could use <code>df_can['2013'].plot.hist()</code>, instead. In fact, throughout this lesson, using <code>some_data.plot(kind='type_plot', ...)</code> is equivalent to <code>some_data.plot.type_plot(...)</code>. That is, passing the type of the plot as argument or method behaves the same.</p>
<p>See the <em>pandas</em> documentation for more info  <a href="http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.plot.html">http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.plot.html</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can also plot multiple histograms on the same plot. For example, let's try to answer the following questions using a histogram.</p>
<p><strong>Question</strong>: <strong>What is the immigration distribution for Denmark, Norway, and Sweden for years 1980 - 2013?</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># let&#39;s quickly view the dataset </span>
<span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Denmark&#39;</span><span class="p">,</span> <span class="s1">&#39;Norway&#39;</span><span class="p">,</span> <span class="s1">&#39;Sweden&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># generate histogram</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Denmark&#39;</span><span class="p">,</span> <span class="s1">&#39;Norway&#39;</span><span class="p">,</span> <span class="s1">&#39;Sweden&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="o">.</span><span class="n">hist</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>That does not look right!</p>
<p>Don't worry, you'll often come across situations like this when creating plots. The solution often lies in how the underlying dataset is structured.</p>
<p>Instead of plotting the population frequency distribution of the population for the 3 countries, <em>Pandas</em> instead plotted the population frequency distribution for the <code>years</code>.</p>
<p>This can be easily fixed by first transposing the dataset, and then plotting as shown below.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># transpose dataframe</span>
<span class="n">df_t</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Denmark&#39;</span><span class="p">,</span> <span class="s1">&#39;Norway&#39;</span><span class="p">,</span> <span class="s1">&#39;Sweden&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span>
<span class="n">df_t</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># generate histogram</span>
<span class="n">df_t</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;hist&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Histogram of Immigration from Denmark, Norway, and Sweden from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Years&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's make a few modifications to improve the impact and aesthetics of the previous plot:</p>
<ul>
<li>increase the bin size to 15 by passing in <code>bins</code> parameter</li>
<li>set transparency to 60% by passing in <code>alpha</code> paramemter</li>
<li>label the x-axis by passing in <code>x-label</code> paramater</li>
<li>change the colors of the plots by passing in <code>color</code> parameter</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># let&#39;s get the x-tick values</span>
<span class="n">count</span><span class="p">,</span> <span class="n">bin_edges</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">histogram</span><span class="p">(</span><span class="n">df_t</span><span class="p">,</span> <span class="mi">15</span><span class="p">)</span>

<span class="c1"># un-stacked histogram</span>
<span class="n">df_t</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span> <span class="o">=</span><span class="s1">&#39;hist&#39;</span><span class="p">,</span> 
          <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span>
          <span class="n">bins</span><span class="o">=</span><span class="mi">15</span><span class="p">,</span>
          <span class="n">alpha</span><span class="o">=</span><span class="mf">0.6</span><span class="p">,</span>
          <span class="n">xticks</span><span class="o">=</span><span class="n">bin_edges</span><span class="p">,</span>
          <span class="n">color</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;coral&#39;</span><span class="p">,</span> <span class="s1">&#39;darkslateblue&#39;</span><span class="p">,</span> <span class="s1">&#39;mediumseagreen&#39;</span><span class="p">]</span>
         <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Histogram of Immigration from Denmark, Norway, and Sweden from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Years&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Tip:
For a full listing of colors available in Matplotlib, run the following code in your python shell:</p>
<div class="highlight"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib</span>
<span class="k">for</span> <span class="n">name</span><span class="p">,</span> <span class="nb">hex</span> <span class="ow">in</span> <span class="n">matplotlib</span><span class="o">.</span><span class="n">colors</span><span class="o">.</span><span class="n">cnames</span><span class="o">.</span><span class="n">items</span><span class="p">():</span>
    <span class="k">print</span><span class="p">(</span><span class="n">name</span><span class="p">,</span> <span class="nb">hex</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>If we do no want the plots to overlap each other, we can stack them using the <code>stacked</code> paramemter. Let's also adjust the min and max x-axis labels to remove the extra gap on the edges of the plot. We can pass a tuple (min,max) using the <code>xlim</code> paramater, as show below.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">count</span><span class="p">,</span> <span class="n">bin_edges</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">histogram</span><span class="p">(</span><span class="n">df_t</span><span class="p">,</span> <span class="mi">15</span><span class="p">)</span>
<span class="n">xmin</span> <span class="o">=</span> <span class="n">bin_edges</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">-</span> <span class="mi">10</span>   <span class="c1">#  first bin value is 31.0, adding buffer of 10 for aesthetic purposes </span>
<span class="n">xmax</span> <span class="o">=</span> <span class="n">bin_edges</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">+</span> <span class="mi">10</span>  <span class="c1">#  last bin value is 308.0, adding buffer of 10 for aesthetic purposes</span>

<span class="c1"># stacked Histogram</span>
<span class="n">df_t</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;hist&#39;</span><span class="p">,</span>
          <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> 
          <span class="n">bins</span><span class="o">=</span><span class="mi">15</span><span class="p">,</span>
          <span class="n">xticks</span><span class="o">=</span><span class="n">bin_edges</span><span class="p">,</span>
          <span class="n">color</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;coral&#39;</span><span class="p">,</span> <span class="s1">&#39;darkslateblue&#39;</span><span class="p">,</span> <span class="s1">&#39;mediumseagreen&#39;</span><span class="p">],</span>
          <span class="n">stacked</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
          <span class="n">xlim</span><span class="o">=</span><span class="p">(</span><span class="n">xmin</span><span class="p">,</span> <span class="n">xmax</span><span class="p">)</span>
         <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Histogram of Immigration from Denmark, Norway, and Sweden from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Years&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span> 

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: <strong>Use the scripting layer to display the immigration distribution for Greece, Albania, and Bulgaria for years 1980 - 2013? Use an overlapping plot with 15 bins and a transparency value of 0.35.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># create a dataframe of the countries of interest (cof)</span>
<span class="n">df_cof</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Greece&#39;</span><span class="p">,</span> <span class="s1">&#39;Albania&#39;</span><span class="p">,</span> <span class="s1">&#39;Bulgaria&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span>

<span class="c1"># transpose the dataframe</span>
<span class="n">df_cof</span> <span class="o">=</span> <span class="n">df_cof</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> 

<span class="c1"># let&#39;s get the x-tick values</span>
<span class="n">count</span><span class="p">,</span> <span class="n">bin_edges</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">histogram</span><span class="p">(</span><span class="n">df_cof</span><span class="p">,</span> <span class="mi">15</span><span class="p">)</span>

<span class="c1"># Un-stacked Histogram</span>
<span class="n">df_cof</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span> <span class="o">=</span><span class="s1">&#39;hist&#39;</span><span class="p">,</span>
            <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span>
            <span class="n">bins</span><span class="o">=</span><span class="mi">15</span><span class="p">,</span>
            <span class="n">alpha</span><span class="o">=</span><span class="mf">0.35</span><span class="p">,</span>
            <span class="n">xticks</span><span class="o">=</span><span class="n">bin_edges</span><span class="p">,</span>
            <span class="n">color</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;coral&#39;</span><span class="p">,</span> <span class="s1">&#39;darkslateblue&#39;</span><span class="p">,</span> <span class="s1">&#39;mediumseagreen&#39;</span><span class="p">]</span>
            <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Histogram of Immigration from Greece, Albania, and Bulgaria from 1980 - 2013&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Years&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.9 Bar-Charts-(Dataframe)-">2.9 Bar Charts (Dataframe) <a id="10" /><a class="anchor-link" href="#2.9 Bar-Charts-(Dataframe)-">&#182;</a></h2><p>A bar plot is a way of representing data where the <em>length</em> of the bars represents the magnitude/size of the feature/variable. Bar graphs usually represent numerical and categorical variables grouped in intervals.</p>
<p>To create a bar plot, we can pass one of two arguments via <code>kind</code> parameter in <code>plot()</code>:</p>
<ul>
<li><code>kind=bar</code> creates a <em>vertical</em> bar plot</li>
<li><code>kind=barh</code> creates a <em>horizontal</em> bar plot</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Vertical bar plot</strong></p>
<p>In vertical bar graphs, the x-axis is used for labelling, and the length of bars on the y-axis corresponds to the magnitude of the variable being measured. Vertical bar graphs are particuarly useful in analyzing time series data. One disadvantage is that they lack space for text labelling at the foot of each bar.</p>
<p><strong>Let's start off by analyzing the effect of Iceland's Financial Crisis:</strong></p>
<p>The 2008 - 2011 Icelandic Financial Crisis was a major economic and political event in Iceland. Relative to the size of its economy, Iceland's systemic banking collapse was the largest experienced by any country in economic history. The crisis led to a severe economic depression in 2008 - 2011 and significant political unrest.</p>
<p><strong>Question:</strong> <strong>Let's compare the number of Icelandic immigrants (country = 'Iceland') to Canada from year 1980 to 2013.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># step 1: get the data</span>
<span class="n">df_iceland</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="s1">&#39;Iceland&#39;</span><span class="p">,</span> <span class="n">years</span><span class="p">]</span>
<span class="n">df_iceland</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># step 2: plot data</span>
<span class="n">df_iceland</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">))</span>

<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Year&#39;</span><span class="p">)</span> <span class="c1"># add to x-label to the plot</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of immigrants&#39;</span><span class="p">)</span> <span class="c1"># add y-label to the plot</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Icelandic immigrants to Canada from 1980 to 2013&#39;</span><span class="p">)</span> <span class="c1"># add title to the plot</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The bar plot above shows the total number of immigrants broken down by each year. We can clearly see the impact of the financial crisis; the number of immigrants to Canada started increasing rapidly after 2008.</p>
<p>Let's annotate this on the plot using the <code>annotate</code> method of the <strong>scripting layer</strong> or the <strong>pyplot interface</strong>. We will pass in the following parameters:</p>
<ul>
<li><code>s</code>: str, the text of annotation.</li>
<li><code>xy</code>: Tuple specifying the (x,y) point to annotate (in this case, end point of arrow).</li>
<li><code>xytext</code>: Tuple specifying the (x,y) point to place the text (in this case, start point of arrow).</li>
<li><code>xycoords</code>: The coordinate system that xy is given in - 'data' uses the coordinate system of the object being annotated (default).</li>
<li><code>arrowprops</code>: Takes a dictionary of properties to draw the arrow:<ul>
<li><code>arrowstyle</code>: Specifies the arrow style, <code>'-&gt;'</code> is standard arrow.</li>
<li><code>connectionstyle</code>: Specifies the connection type. <code>arc3</code> is a straight line.</li>
<li><code>color</code>: Specifes color of arror.</li>
<li><code>lw</code>: Specifies the line width.</li>
</ul>
</li>
</ul>
<p>I encourage you to read the Matplotlib documentation for more details on annotations: 
<a href="http://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.annotate">http://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.annotate</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_iceland</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> <span class="n">rot</span><span class="o">=</span><span class="mi">90</span><span class="p">)</span> <span class="c1"># rotate the bars by 90 degrees</span>

<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Year&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Icelandic Immigrants to Canada from 1980 to 2013&#39;</span><span class="p">)</span>

<span class="c1"># Annotate arrow</span>
<span class="n">plt</span><span class="o">.</span><span class="n">annotate</span><span class="p">(</span><span class="s1">&#39;&#39;</span><span class="p">,</span>                      <span class="c1"># s: str. Will leave it blank for no text</span>
             <span class="n">xy</span><span class="o">=</span><span class="p">(</span><span class="mi">32</span><span class="p">,</span> <span class="mi">70</span><span class="p">),</span>             <span class="c1"># place head of the arrow at point (year 2012 , pop 70)</span>
             <span class="n">xytext</span><span class="o">=</span><span class="p">(</span><span class="mi">28</span><span class="p">,</span> <span class="mi">20</span><span class="p">),</span>         <span class="c1"># place base of the arrow at point (year 2008 , pop 20)</span>
             <span class="n">xycoords</span><span class="o">=</span><span class="s1">&#39;data&#39;</span><span class="p">,</span>         <span class="c1"># will use the coordinate system of the object being annotated </span>
             <span class="n">arrowprops</span><span class="o">=</span><span class="nb">dict</span><span class="p">(</span><span class="n">arrowstyle</span><span class="o">=</span><span class="s1">&#39;-&gt;&#39;</span><span class="p">,</span> <span class="n">connectionstyle</span><span class="o">=</span><span class="s1">&#39;arc3&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span> <span class="n">lw</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
            <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's also annotate a text to go over the arrow.  We will pass in the following additional parameters:</p>
<ul>
<li><code>rotation</code>: rotation angle of text in degrees (counter clockwise)</li>
<li><code>va</code>: vertical alignment of text [‘center’ | ‘top’ | ‘bottom’ | ‘baseline’]</li>
<li><code>ha</code>: horizontal alignment of text [‘center’ | ‘right’ | ‘left’]</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_iceland</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">),</span> <span class="n">rot</span><span class="o">=</span><span class="mi">90</span><span class="p">)</span> 

<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Year&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Icelandic Immigrants to Canada from 1980 to 2013&#39;</span><span class="p">)</span>

<span class="c1"># Annotate arrow</span>
<span class="n">plt</span><span class="o">.</span><span class="n">annotate</span><span class="p">(</span><span class="s1">&#39;&#39;</span><span class="p">,</span>                      <span class="c1"># s: str. will leave it blank for no text</span>
             <span class="n">xy</span><span class="o">=</span><span class="p">(</span><span class="mi">32</span><span class="p">,</span> <span class="mi">70</span><span class="p">),</span>             <span class="c1"># place head of the arrow at point (year 2012 , pop 70)</span>
             <span class="n">xytext</span><span class="o">=</span><span class="p">(</span><span class="mi">28</span><span class="p">,</span> <span class="mi">20</span><span class="p">),</span>         <span class="c1"># place base of the arrow at point (year 2008 , pop 20)</span>
             <span class="n">xycoords</span><span class="o">=</span><span class="s1">&#39;data&#39;</span><span class="p">,</span>         <span class="c1"># will use the coordinate system of the object being annotated </span>
             <span class="n">arrowprops</span><span class="o">=</span><span class="nb">dict</span><span class="p">(</span><span class="n">arrowstyle</span><span class="o">=</span><span class="s1">&#39;-&gt;&#39;</span><span class="p">,</span> <span class="n">connectionstyle</span><span class="o">=</span><span class="s1">&#39;arc3&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span> <span class="n">lw</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
            <span class="p">)</span>

<span class="c1"># Annotate Text</span>
<span class="n">plt</span><span class="o">.</span><span class="n">annotate</span><span class="p">(</span><span class="s1">&#39;2008 - 2011 Financial Crisis&#39;</span><span class="p">,</span> <span class="c1"># text to display</span>
             <span class="n">xy</span><span class="o">=</span><span class="p">(</span><span class="mi">28</span><span class="p">,</span> <span class="mi">30</span><span class="p">),</span>                    <span class="c1"># start the text at at point (year 2008 , pop 30)</span>
             <span class="n">rotation</span><span class="o">=</span><span class="mf">72.5</span><span class="p">,</span>                  <span class="c1"># based on trial and error to match the arrow</span>
             <span class="n">va</span><span class="o">=</span><span class="s1">&#39;bottom&#39;</span><span class="p">,</span>                    <span class="c1"># want the text to be vertically &#39;bottom&#39; aligned</span>
             <span class="n">ha</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span>                      <span class="c1"># want the text to be horizontally &#39;left&#39; algned.</span>
            <span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Horizontal Bar Plot</strong></p>
<p>Sometimes it is more practical to represent the data horizontally, especially if you need more room for labelling the bars. In horizontal bar graphs, the y-axis is used for labelling, and the length of bars on the x-axis corresponds to the magnitude of the variable being measured. As you will see, there is more room on the y-axis to  label categetorical variables.</p>
<p><strong>Question:</strong> <strong>Using the scripting layter and the <code>df_can</code> dataset, create a <em>horizontal</em> bar plot showing the <em>total</em> number of immigrants to Canada from the top 15 countries, for the period 1980 - 2013. Label each country with the total immigrant count.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 1: Get the data pertaining to the top 15 countries.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># sort dataframe on &#39;Total&#39; column (descending)</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">by</span><span class="o">=</span><span class="s1">&#39;Total&#39;</span><span class="p">,</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># get top 15 countries</span>
<span class="n">df_top15</span> <span class="o">=</span> <span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">tail</span><span class="p">(</span><span class="mi">15</span><span class="p">)</span>
<span class="n">df_top15</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step 2: Plot data:</p>
<ol>
<li>Use <code>kind='barh'</code> to generate a bar chart with horizontal bars.</li>
<li>Make sure to choose a good size for the plot and to label your axes and to give the plot a title.</li>
<li>Loop through the countries and annotate the immigrant population using the anotate function of the scripting interface.</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># generate plot</span>
<span class="n">df_top15</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;barh&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span> <span class="mi">12</span><span class="p">),</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;steelblue&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of Immigrants&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Top 15 Conuntries Contributing to the Immigration to Canada between 1980 - 2013&#39;</span><span class="p">)</span>

<span class="c1"># annotate value labels to each country</span>
<span class="k">for</span> <span class="n">index</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">df_top15</span><span class="p">):</span> 
    <span class="n">label</span> <span class="o">=</span> <span class="nb">format</span><span class="p">(</span><span class="nb">int</span><span class="p">(</span><span class="n">value</span><span class="p">),</span> <span class="s1">&#39;,&#39;</span><span class="p">)</span> <span class="c1"># format int with commas</span>
    
<span class="c1"># place text at the end of bar (subtracting 47000 from x, and 0.1 from y to make it fit within the bar)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">annotate</span><span class="p">(</span><span class="n">label</span><span class="p">,</span> <span class="n">xy</span><span class="o">=</span><span class="p">(</span><span class="n">value</span> <span class="o">-</span> <span class="mi">47000</span><span class="p">,</span> <span class="n">index</span> <span class="o">-</span> <span class="mf">0.10</span><span class="p">),</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;white&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.10 Waffle-Charts-">2.10 Waffle Charts <a id="6" /><a class="anchor-link" href="#2.10 Waffle-Charts-">&#182;</a></h2><p>A <code>waffle chart</code> is an interesting visualization that is normally created to display progress toward goals. It is commonly an effective option when you are trying to add interesting visualization features to a visual that consists mainly of cells, such as an Excel dashboard.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's revisit the previous case study about Denmark, Norway, and Sweden.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># let&#39;s create a new dataframe for these three countries </span>
<span class="n">df_dsn</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Denmark&#39;</span><span class="p">,</span> <span class="s1">&#39;Norway&#39;</span><span class="p">,</span> <span class="s1">&#39;Sweden&#39;</span><span class="p">],</span> <span class="p">:]</span>

<span class="c1"># let&#39;s take a look at our dataframe</span>
<span class="n">df_dsn</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Unfortunately, unlike R, <code>waffle</code> charts are not built into any of the Python visualization libraries. Therefore, we will learn how to create them from scratch.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Step 1.</strong> The first step into creating a waffle chart is determing the proportion of each category with respect to the total.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># compute the proportion of each category with respect to the total</span>
<span class="n">total_values</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">df_dsn</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">])</span>
<span class="n">category_proportions</span> <span class="o">=</span> <span class="p">[(</span><span class="nb">float</span><span class="p">(</span><span class="n">value</span><span class="p">)</span> <span class="o">/</span> <span class="n">total_values</span><span class="p">)</span> <span class="k">for</span> <span class="n">value</span> <span class="ow">in</span> <span class="n">df_dsn</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]]</span>

<span class="c1"># print out proportions</span>
<span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">proportion</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">category_proportions</span><span class="p">):</span>
    <span class="nb">print</span> <span class="p">(</span><span class="n">df_dsn</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">+</span> <span class="s1">&#39;: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">proportion</span><span class="p">))</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Step 2.</strong> The second step is defining the overall size of the <code>waffle</code> chart.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">width</span> <span class="o">=</span> <span class="mi">40</span> <span class="c1"># width of chart</span>
<span class="n">height</span> <span class="o">=</span> <span class="mi">10</span> <span class="c1"># height of chart</span>

<span class="n">total_num_tiles</span> <span class="o">=</span> <span class="n">width</span> <span class="o">*</span> <span class="n">height</span> <span class="c1"># total number of tiles</span>

<span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;Total number of tiles is &#39;</span><span class="p">,</span> <span class="n">total_num_tiles</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Step 3.</strong> The third step is using the proportion of each category to determe it respective number of tiles</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># compute the number of tiles for each catagory</span>
<span class="n">tiles_per_category</span> <span class="o">=</span> <span class="p">[</span><span class="nb">round</span><span class="p">(</span><span class="n">proportion</span> <span class="o">*</span> <span class="n">total_num_tiles</span><span class="p">)</span> <span class="k">for</span> <span class="n">proportion</span> <span class="ow">in</span> <span class="n">category_proportions</span><span class="p">]</span>

<span class="c1"># print out number of tiles per category</span>
<span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">tiles</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">tiles_per_category</span><span class="p">):</span>
    <span class="nb">print</span> <span class="p">(</span><span class="n">df_dsn</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">+</span> <span class="s1">&#39;: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">tiles</span><span class="p">))</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Based on the calculated proportions, Denmark will occupy 129 tiles of the <code>waffle</code> chart, Norway will occupy 77 tiles, and Sweden will occupy 194 tiles.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Step 4.</strong> The fourth step is creating a matrix that resembles the <code>waffle</code> chart and populating it.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># initialize the waffle chart as an empty matrix</span>
<span class="n">waffle_chart</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="n">height</span><span class="p">,</span> <span class="n">width</span><span class="p">))</span>

<span class="c1"># define indices to loop through waffle chart</span>
<span class="n">category_index</span> <span class="o">=</span> <span class="mi">0</span>
<span class="n">tile_index</span> <span class="o">=</span> <span class="mi">0</span>

<span class="c1"># populate the waffle chart</span>
<span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">width</span><span class="p">):</span>
    <span class="k">for</span> <span class="n">row</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">height</span><span class="p">):</span>
        <span class="n">tile_index</span> <span class="o">+=</span> <span class="mi">1</span>

 <span class="c1"># if the number of tiles populated for the current category is equal to its corresponding allocated tiles...</span>
        <span class="k">if</span> <span class="n">tile_index</span> <span class="o">&gt;</span> <span class="nb">sum</span><span class="p">(</span><span class="n">tiles_per_category</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="n">category_index</span><span class="p">]):</span>
            <span class="c1"># ...proceed to the next category</span>
            <span class="n">category_index</span> <span class="o">+=</span> <span class="mi">1</span>       
            
 <span class="c1"># set the class value to an integer, which increases with class</span>
        <span class="n">waffle_chart</span><span class="p">[</span><span class="n">row</span><span class="p">,</span> <span class="n">col</span><span class="p">]</span> <span class="o">=</span> <span class="n">category_index</span>
        
<span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;Waffle chart populated!&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's take a peek at how the matrix looks like.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">waffle_chart</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As expected, the matrix consists of three categories and the total number of each category's instances matches the total number of tiles allocated to each category.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Step 5.</strong> Map the <code>waffle</code> chart matrix into a visual.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># instantiate a new figure object</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>

<span class="c1"># use matshow to display the waffle chart</span>
<span class="n">colormap</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">cm</span><span class="o">.</span><span class="n">coolwarm</span>
<span class="n">plt</span><span class="o">.</span><span class="n">matshow</span><span class="p">(</span><span class="n">waffle_chart</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="n">colormap</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">colorbar</span><span class="p">()</span>
</pre></div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Step 6.</strong> Prettify the chart.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># instantiate a new figure object</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>

<span class="c1"># use matshow to display the waffle chart</span>
<span class="n">colormap</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">cm</span><span class="o">.</span><span class="n">coolwarm</span>
<span class="n">plt</span><span class="o">.</span><span class="n">matshow</span><span class="p">(</span><span class="n">waffle_chart</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="n">colormap</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">colorbar</span><span class="p">()</span>

<span class="c1"># get the axis</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">gca</span><span class="p">()</span>

<span class="c1"># set minor ticks</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_xticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="o">-.</span><span class="mi">5</span><span class="p">,</span> <span class="p">(</span><span class="n">width</span><span class="p">),</span> <span class="mi">1</span><span class="p">),</span> <span class="n">minor</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_yticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="o">-.</span><span class="mi">5</span><span class="p">,</span> <span class="p">(</span><span class="n">height</span><span class="p">),</span> <span class="mi">1</span><span class="p">),</span> <span class="n">minor</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    
<span class="c1"># add gridlines based on minor ticks</span>
<span class="n">ax</span><span class="o">.</span><span class="n">grid</span><span class="p">(</span><span class="n">which</span><span class="o">=</span><span class="s1">&#39;minor&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;w&#39;</span><span class="p">,</span> <span class="n">linestyle</span><span class="o">=</span><span class="s1">&#39;-&#39;</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">([])</span>
<span class="n">plt</span><span class="o">.</span><span class="n">yticks</span><span class="p">([])</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Step 7.</strong> Create a legend and add it to chart.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># instantiate a new figure object</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>

<span class="c1"># use matshow to display the waffle chart</span>
<span class="n">colormap</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">cm</span><span class="o">.</span><span class="n">coolwarm</span>
<span class="n">plt</span><span class="o">.</span><span class="n">matshow</span><span class="p">(</span><span class="n">waffle_chart</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="n">colormap</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">colorbar</span><span class="p">()</span>

<span class="c1"># get the axis</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">gca</span><span class="p">()</span>

<span class="c1"># set minor ticks</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_xticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="o">-.</span><span class="mi">5</span><span class="p">,</span> <span class="p">(</span><span class="n">width</span><span class="p">),</span> <span class="mi">1</span><span class="p">),</span> <span class="n">minor</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_yticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="o">-.</span><span class="mi">5</span><span class="p">,</span> <span class="p">(</span><span class="n">height</span><span class="p">),</span> <span class="mi">1</span><span class="p">),</span> <span class="n">minor</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    
<span class="c1"># add gridlines based on minor ticks</span>
<span class="n">ax</span><span class="o">.</span><span class="n">grid</span><span class="p">(</span><span class="n">which</span><span class="o">=</span><span class="s1">&#39;minor&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;w&#39;</span><span class="p">,</span> <span class="n">linestyle</span><span class="o">=</span><span class="s1">&#39;-&#39;</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">([])</span>
<span class="n">plt</span><span class="o">.</span><span class="n">yticks</span><span class="p">([])</span>

<span class="c1"># compute cumulative sum of individual categories to match color schemes between chart and legend</span>
<span class="n">values_cumsum</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">cumsum</span><span class="p">(</span><span class="n">df_dsn</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">])</span>
<span class="n">total_values</span> <span class="o">=</span> <span class="n">values_cumsum</span><span class="p">[</span><span class="nb">len</span><span class="p">(</span><span class="n">values_cumsum</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span><span class="p">]</span>

<span class="c1"># create legend</span>
<span class="n">legend_handles</span> <span class="o">=</span> <span class="p">[]</span>
<span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">category</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">df_dsn</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">):</span>
    <span class="n">label_str</span> <span class="o">=</span> <span class="n">category</span> <span class="o">+</span> <span class="s1">&#39; (&#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">df_dsn</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">][</span><span class="n">i</span><span class="p">])</span> <span class="o">+</span> <span class="s1">&#39;)&#39;</span>
    <span class="n">color_val</span> <span class="o">=</span> <span class="n">colormap</span><span class="p">(</span><span class="nb">float</span><span class="p">(</span><span class="n">values_cumsum</span><span class="p">[</span><span class="n">i</span><span class="p">])</span><span class="o">/</span><span class="n">total_values</span><span class="p">)</span>
    
<span class="c1"># add legend to chart</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">handles</span><span class="o">=</span><span class="n">legend_handles</span><span class="p">,</span>
           <span class="n">loc</span><span class="o">=</span><span class="s1">&#39;lower center&#39;</span><span class="p">,</span> 
           <span class="n">ncol</span><span class="o">=</span><span class="nb">len</span><span class="p">(</span><span class="n">df_dsn</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">),</span>
           <span class="n">bbox_to_anchor</span><span class="o">=</span><span class="p">(</span><span class="mf">0.</span><span class="p">,</span> <span class="o">-</span><span class="mf">0.2</span><span class="p">,</span> <span class="mf">0.95</span><span class="p">,</span> <span class="o">.</span><span class="mi">1</span><span class="p">)</span>
          <span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>And there you go! What a good looking <em>delicious</em> <code>waffle</code> chart, don't you think?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now it would very inefficient to repeat these seven steps every time we wish to create a <code>waffle</code> chart. So let's combine all seven steps into one function called <em>create_waffle_chart</em>. This function would take the following parameters as input:</p>
<blockquote><ol>
<li><strong>categories</strong>: Unique categories or classes in dataframe.</li>
<li><strong>values</strong>: Values corresponding to categories or classes.</li>
<li><strong>height</strong>: Defined height of waffle chart.</li>
<li><strong>width</strong>: Defined width of waffle chart.</li>
<li><strong>colormap</strong>: Colormap class</li>
<li><strong>value_sign</strong>: In order to make our function more generalizable, we will add this parameter to address signs that could be associated with a value such as %, $, and so on. <strong>value_sign</strong> has a default value of empty string.</li>
</ol>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">create_waffle_chart</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">values</span><span class="p">,</span> <span class="n">height</span><span class="p">,</span> <span class="n">width</span><span class="p">,</span> <span class="n">colormap</span><span class="p">,</span> <span class="n">value_sign</span><span class="o">=</span><span class="s1">&#39;&#39;</span><span class="p">):</span>

   <span class="c1"># compute the proportion of each category with respect to the total</span>
    <span class="n">total_values</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">values</span><span class="p">)</span>
    <span class="n">category_proportions</span> <span class="o">=</span> <span class="p">[(</span><span class="nb">float</span><span class="p">(</span><span class="n">value</span><span class="p">)</span> <span class="o">/</span> <span class="n">total_values</span><span class="p">)</span> <span class="k">for</span> <span class="n">value</span> <span class="ow">in</span> <span class="n">values</span><span class="p">]</span>

  <span class="c1"># compute the total number of tiles</span>
    <span class="n">total_num_tiles</span> <span class="o">=</span> <span class="n">width</span> <span class="o">*</span> <span class="n">height</span> <span class="c1"># total number of tiles</span>
    <span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;Total number of tiles is&#39;</span><span class="p">,</span> <span class="n">total_num_tiles</span><span class="p">)</span>
    
  <span class="c1"># compute the number of tiles for each catagory</span>
    <span class="n">tiles_per_category</span> <span class="o">=</span> <span class="p">[</span><span class="nb">round</span><span class="p">(</span><span class="n">proportion</span> <span class="o">*</span> <span class="n">total_num_tiles</span><span class="p">)</span> <span class="k">for</span> <span class="n">proportion</span> <span class="ow">in</span> <span class="n">category_proportions</span><span class="p">]</span>

  <span class="c1"># print out number of tiles per category</span>
    <span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">tiles</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">tiles_per_category</span><span class="p">):</span>
        <span class="nb">print</span> <span class="p">(</span><span class="n">df_dsn</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">+</span> <span class="s1">&#39;: &#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">tiles</span><span class="p">))</span>
    
  <span class="c1"># initialize the waffle chart as an empty matrix</span>
    <span class="n">waffle_chart</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="n">height</span><span class="p">,</span> <span class="n">width</span><span class="p">))</span>

  <span class="c1"># define indices to loop through waffle chart</span>
    <span class="n">category_index</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="n">tile_index</span> <span class="o">=</span> <span class="mi">0</span>

  <span class="c1"># populate the waffle chart</span>
    <span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">width</span><span class="p">):</span>
        <span class="k">for</span> <span class="n">row</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">height</span><span class="p">):</span>
            <span class="n">tile_index</span> <span class="o">+=</span> <span class="mi">1</span>

  <span class="c1"># if the number of tiles populated for the current category </span>
            <span class="c1"># is equal to its corresponding allocated tiles...</span>
            <span class="k">if</span> <span class="n">tile_index</span> <span class="o">&gt;</span> <span class="nb">sum</span><span class="p">(</span><span class="n">tiles_per_category</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="n">category_index</span><span class="p">]):</span>
                <span class="c1"># ...proceed to the next category</span>
                <span class="n">category_index</span> <span class="o">+=</span> <span class="mi">1</span>       
            
   <span class="c1"># set the class value to an integer, which increases with class</span>
            <span class="n">waffle_chart</span><span class="p">[</span><span class="n">row</span><span class="p">,</span> <span class="n">col</span><span class="p">]</span> <span class="o">=</span> <span class="n">category_index</span>
    
 <span class="c1"># instantiate a new figure object</span>
    <span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>

<span class="c1"># use matshow to display the waffle chart</span>
    <span class="n">colormap</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">cm</span><span class="o">.</span><span class="n">coolwarm</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">matshow</span><span class="p">(</span><span class="n">waffle_chart</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="n">colormap</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">colorbar</span><span class="p">()</span>

<span class="c1"># get the axis</span>
    <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">gca</span><span class="p">()</span>

<span class="c1"># set minor ticks</span>
    <span class="n">ax</span><span class="o">.</span><span class="n">set_xticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="o">-.</span><span class="mi">5</span><span class="p">,</span> <span class="p">(</span><span class="n">width</span><span class="p">),</span> <span class="mi">1</span><span class="p">),</span> <span class="n">minor</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">ax</span><span class="o">.</span><span class="n">set_yticks</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="o">-.</span><span class="mi">5</span><span class="p">,</span> <span class="p">(</span><span class="n">height</span><span class="p">),</span> <span class="mi">1</span><span class="p">),</span> <span class="n">minor</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    
<span class="c1"># add dridlines based on minor ticks</span>
    <span class="n">ax</span><span class="o">.</span><span class="n">grid</span><span class="p">(</span><span class="n">which</span><span class="o">=</span><span class="s1">&#39;minor&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;w&#39;</span><span class="p">,</span> <span class="n">linestyle</span><span class="o">=</span><span class="s1">&#39;-&#39;</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>

  <span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">([])</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">yticks</span><span class="p">([])</span>

 <span class="c1"># compute cumulative sum of individual categories to match color schemes between chart and legend</span>
    <span class="n">values_cumsum</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">cumsum</span><span class="p">(</span><span class="n">values</span><span class="p">)</span>
    <span class="n">total_values</span> <span class="o">=</span> <span class="n">values_cumsum</span><span class="p">[</span><span class="nb">len</span><span class="p">(</span><span class="n">values_cumsum</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span><span class="p">]</span>

  <span class="c1"># create legend</span>
    <span class="n">legend_handles</span> <span class="o">=</span> <span class="p">[]</span>
    <span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">category</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">categories</span><span class="p">):</span>
        <span class="k">if</span> <span class="n">value_sign</span> <span class="o">==</span> <span class="s1">&#39;%&#39;</span><span class="p">:</span>
            <span class="n">label_str</span> <span class="o">=</span> <span class="n">category</span> <span class="o">+</span> <span class="s1">&#39; (&#39;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">values</span><span class="p">[</span><span class="n">i</span><span class="p">])</span> <span class="o">+</span> <span class="n">value_sign</span> <span class="o">+</span> <span class="s1">&#39;)&#39;</span>
        <span class="k">else</span><span class="p">:</span>
            <span class="n">label_str</span> <span class="o">=</span> <span class="n">category</span> <span class="o">+</span> <span class="s1">&#39; (&#39;</span> <span class="o">+</span> <span class="n">value_sign</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">values</span><span class="p">[</span><span class="n">i</span><span class="p">])</span> <span class="o">+</span> <span class="s1">&#39;)&#39;</span>
            
  <span class="n">color_val</span> <span class="o">=</span> <span class="n">colormap</span><span class="p">(</span><span class="nb">float</span><span class="p">(</span><span class="n">values_cumsum</span><span class="p">[</span><span class="n">i</span><span class="p">])</span><span class="o">/</span><span class="n">total_values</span><span class="p">)</span>
        
<span class="c1"># add legend to chart</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span>
        <span class="n">handles</span><span class="o">=</span><span class="n">legend_handles</span><span class="p">,</span>
        <span class="n">loc</span><span class="o">=</span><span class="s1">&#39;lower center&#39;</span><span class="p">,</span> 
        <span class="n">ncol</span><span class="o">=</span><span class="nb">len</span><span class="p">(</span><span class="n">categories</span><span class="p">),</span>
        <span class="n">bbox_to_anchor</span><span class="o">=</span><span class="p">(</span><span class="mf">0.</span><span class="p">,</span> <span class="o">-</span><span class="mf">0.2</span><span class="p">,</span> <span class="mf">0.95</span><span class="p">,</span> <span class="o">.</span><span class="mi">1</span><span class="p">)</span>
    <span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now to create a <code>waffle</code> chart, all we have to do is call the function <code>create_waffle_chart</code>. Let's define the input parameters:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">width</span> <span class="o">=</span> <span class="mi">40</span> <span class="c1"># width of chart</span>
<span class="n">height</span> <span class="o">=</span> <span class="mi">10</span> <span class="c1"># height of chart</span>

<span class="n">categories</span> <span class="o">=</span> <span class="n">df_dsn</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span> <span class="c1"># categories</span>
<span class="n">values</span> <span class="o">=</span> <span class="n">df_dsn</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span> <span class="c1"># correponding values of categories</span>

<span class="n">colormap</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">cm</span><span class="o">.</span><span class="n">coolwarm</span> <span class="c1"># color map class</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>And now let's call our function to create a <code>waffle</code> chart.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">create_waffle_chart</span><span class="p">(</span><span class="n">categories</span><span class="p">,</span> <span class="n">values</span><span class="p">,</span> <span class="n">height</span><span class="p">,</span> <span class="n">width</span><span class="p">,</span> <span class="n">colormap</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>There seems to be a new Python package for generating <code>waffle charts</code> called <a href="https://github.com/ligyxy/PyWaffle">PyWaffle</a>, but the repository has barely any documentation on the package. Accordingly, I couldn't use the package to prepare enough content to incorporate into this lab. But feel free to check it out and play with it. In the event that the package becomes complete with full documentation, then I will update this lab accordingly.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="3. Visualizing-Data-using-word-cloud-">3. Visualizing Data using word cloud <em>Pandas</em> <a id="0" /><a class="anchor-link" href="#3. Visualizing-Data-using-word-cloud-">&#182;</a></h1>
</div>
</div>
</div>

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.1 Word-Clouds-">3.1 Word Clouds <a id="8" /><a class="anchor-link" href="#3.1 Word-Clouds-">&#182;</a></h2><p><code>Word</code> clouds (also known as text clouds or tag clouds) work in a simple way: the more a specific word appears in a source of textual data (such as a speech, blog post, or database), the bigger and bolder it appears in the word cloud.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Luckily, a Python package already exists in Python for generating <code>word</code> clouds. The package, called <code>word_cloud</code> was developed by <strong>Andreas Mueller</strong>. You can learn more about the package by following this <a href="https://github.com/amueller/word_cloud/">link</a>.</p>
<p>Let's use this package to learn how to generate a word cloud for a given text document.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>First, let's install the package.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># install wordcloud</span>
<span class="o">!</span>conda install -c conda-forge <span class="nv">wordcloud</span><span class="o">==</span><span class="m">1</span>.4.1 --yes

<span class="c1"># import package and its set of stopwords</span>
<span class="kn">from</span> <span class="nn">wordcloud</span> <span class="k">import</span> <span class="n">WordCloud</span><span class="p">,</span> <span class="n">STOPWORDS</span>

<span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;Wordcloud is installed and imported!&#39;</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><code>Word</code> clouds are commonly used to perform high-level analysis and visualization of text data. Accordinly, let's digress from the immigration dataset and work with an example that involves analyzing text data. Let's try to analyze a short novel written by <strong>Lewis Carroll</strong> titled <em>Alice's Adventures in Wonderland</em>. Let's go ahead and download a <em>.txt</em> file of the novel.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># download file and save as alice_novel.txt</span>
<span class="o">!</span>wget --quiet https://ibm.box.com/shared/static/m54sjtrshpt5su20dzesl5en9xa5vfz1.txt -O alice_novel.txt

<span class="c1"># open the file and read it into a variable alice_novel</span>
<span class="n">alice_novel</span> <span class="o">=</span> <span class="nb">open</span><span class="p">(</span><span class="s1">&#39;alice_novel.txt&#39;</span><span class="p">,</span> <span class="s1">&#39;r&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">read</span><span class="p">()</span>
    
<span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;File downloaded and saved!&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Next, let's use the stopwords that we imported from <code>word_cloud</code>. We use the function <em>set</em> to remove any redundant stopwords.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">stopwords</span> <span class="o">=</span> <span class="nb">set</span><span class="p">(</span><span class="n">STOPWORDS</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Create a word cloud object and generate a word cloud. For simplicity, let's generate a word cloud using only the first 2000 words in the novel.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># instantiate a word cloud object</span>
<span class="n">alice_wc</span> <span class="o">=</span> <span class="n">WordCloud</span><span class="p">(</span>
    <span class="n">background_color</span><span class="o">=</span><span class="s1">&#39;white&#39;</span><span class="p">,</span>
    <span class="n">max_words</span><span class="o">=</span><span class="mi">2000</span><span class="p">,</span>
    <span class="n">stopwords</span><span class="o">=</span><span class="n">stopwords</span>
<span class="p">)</span>

<span class="c1"># generate the word cloud</span>
<span class="n">alice_wc</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">alice_novel</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Awesome! Now that the <code>word</code> cloud is created, let's visualize it.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># display the word cloud</span>
<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">alice_wc</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;off&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Interesting! So in the first 2000 words in the novel, the most common words are <strong>Alice</strong>, <strong>said</strong>, <strong>little</strong>, <strong>Queen</strong>, and so on. Let's resize the cloud so that we can see the less frequent words a little better.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figwidth</span><span class="p">(</span><span class="mi">14</span><span class="p">)</span> <span class="c1"># set width</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figheight</span><span class="p">(</span><span class="mi">18</span><span class="p">)</span> <span class="c1"># set height</span>

<span class="c1"># display the cloud</span>
<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">alice_wc</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;off&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Much better! However, <strong>said</strong> isn't really an informative word. So let's add it to our stopwords and re-generate the cloud.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">stopwords</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="s1">&#39;said&#39;</span><span class="p">)</span> <span class="c1"># add the words said to stopwords</span>

<span class="c1"># re-generate the word cloud</span>
<span class="n">alice_wc</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">alice_novel</span><span class="p">)</span>

<span class="c1"># display the cloud</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figwidth</span><span class="p">(</span><span class="mi">14</span><span class="p">)</span> <span class="c1"># set width</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figheight</span><span class="p">(</span><span class="mi">18</span><span class="p">)</span> <span class="c1"># set height</span>

<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">alice_wc</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;off&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Excellent! This looks really interesting! Another cool thing you can implement with the <code>word_cloud</code> package is superimposing the words onto a mask of any shape. Let's use a mask of Alice and her rabbit. We already created the mask for you, so let's go ahead and download it and call it <em>alice_mask.png</em>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># download image</span>
<span class="o">!</span>wget --quiet https://ibm.box.com/shared/static/3mpxgaf6muer6af7t1nvqkw9cqj85ibm.png -O alice_mask.png
    
<span class="c1"># save mask to alice_mask</span>
<span class="n">alice_mask</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">Image</span><span class="o">.</span><span class="n">open</span><span class="p">(</span><span class="s1">&#39;alice_mask.png&#39;</span><span class="p">))</span>
    
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Image downloaded and saved!&#39;</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's take a look at how the mask looks like.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figwidth</span><span class="p">(</span><span class="mi">14</span><span class="p">)</span> <span class="c1"># set width</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figheight</span><span class="p">(</span><span class="mi">18</span><span class="p">)</span> <span class="c1"># set height</span>

<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">alice_mask</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="n">plt</span><span class="o">.</span><span class="n">cm</span><span class="o">.</span><span class="n">gray</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;off&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Shaping the <code>word</code> cloud according to the mask is straightforward using <code>word_cloud</code> package. For simplicity, we will continue using the first 2000 words in the novel.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># instantiate a word cloud object</span>
<span class="n">alice_wc</span> <span class="o">=</span> <span class="n">WordCloud</span><span class="p">(</span><span class="n">background_color</span><span class="o">=</span><span class="s1">&#39;white&#39;</span><span class="p">,</span> <span class="n">max_words</span><span class="o">=</span><span class="mi">2000</span><span class="p">,</span> <span class="n">mask</span><span class="o">=</span><span class="n">alice_mask</span><span class="p">,</span> <span class="n">stopwords</span><span class="o">=</span><span class="n">stopwords</span><span class="p">)</span>

<span class="c1"># generate the word cloud</span>
<span class="n">alice_wc</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">alice_novel</span><span class="p">)</span>

<span class="c1"># display the word cloud</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figwidth</span><span class="p">(</span><span class="mi">14</span><span class="p">)</span> <span class="c1"># set width</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figheight</span><span class="p">(</span><span class="mi">18</span><span class="p">)</span> <span class="c1"># set height</span>

<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">alice_wc</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;off&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Really impressive!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Unfortunately, our immmigration data does not have any text data, but where there is a will there is a way. Let's generate sample text data from our immigration dataset, say text data of 90 words.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's recall how our data looks like.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>And what was the total immigration from 1980 to 2013?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">total_immigration</span> <span class="o">=</span> <span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>
<span class="n">total_immigration</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Using countries with single-word names, let's duplicate each country's name based on how much they contribute to the total immigration.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">max_words</span> <span class="o">=</span> <span class="mi">90</span>
<span class="n">word_string</span> <span class="o">=</span> <span class="s1">&#39;&#39;</span>
<span class="k">for</span> <span class="n">country</span> <span class="ow">in</span> <span class="n">df_can</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">:</span>
    <span class="c1"># check if country&#39;s name is a single-word name</span>
    <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">country</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s1">&#39; &#39;</span><span class="p">))</span> <span class="o">==</span> <span class="mi">1</span><span class="p">:</span>
        <span class="n">repeat_num_times</span> <span class="o">=</span> <span class="nb">int</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">country</span><span class="p">,</span> <span class="s1">&#39;Total&#39;</span><span class="p">]</span><span class="o">/</span><span class="nb">float</span><span class="p">(</span><span class="n">total_immigration</span><span class="p">)</span><span class="o">*</span><span class="n">max_words</span><span class="p">)</span>
        <span class="n">word_string</span> <span class="o">=</span> <span class="n">word_string</span> <span class="o">+</span> <span class="p">((</span><span class="n">country</span> <span class="o">+</span> <span class="s1">&#39; &#39;</span><span class="p">)</span> <span class="o">*</span> <span class="n">repeat_num_times</span><span class="p">)</span>
                                     
<span class="c1"># display the generated text</span>
<span class="n">word_string</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We are not dealing with any stopwords here, so there is no need to pass them when creating the word cloud.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># create the word cloud</span>
<span class="n">wordcloud</span> <span class="o">=</span> <span class="n">WordCloud</span><span class="p">(</span><span class="n">background_color</span><span class="o">=</span><span class="s1">&#39;white&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">word_string</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Word cloud created!&#39;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># display the cloud</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figwidth</span><span class="p">(</span><span class="mi">14</span><span class="p">)</span>
<span class="n">fig</span><span class="o">.</span><span class="n">set_figheight</span><span class="p">(</span><span class="mi">18</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">wordcloud</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s1">&#39;off&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>According to the above word cloud, it looks like the majority of the people who immigrated came from one of 15 countries that are displayed by the word cloud. One cool visual that you could build, is perhaps using the map of Canada and a mask and superimposing the word cloud on top of the map of Canada. That would be an interesting visual to build!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="4. Visualizing-Data-using-Seaborn-">4. Visualizing Data using Seaborn <em>Pandas</em> <a id="0" /><a class="anchor-link" href="#4. Visualizing-Data-using-Seaborn-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.1 Regression-Plots-">4.1 Regression Plots <a id="10" /><a class="anchor-link" href="#4.1 Regression-Plots-">&#182;</a></h2><blockquote><p>Seaborn is a Python visualization library based on matplotlib. It provides a high-level interface for drawing attractive statistical graphics. You can learn more about <em>seaborn</em> by following this <a href="https://seaborn.pydata.org/">link</a> and more about <em>seaborn</em> regression plots by following this <a href="http://seaborn.pydata.org/generated/seaborn.regplot.html">link</a>.</p>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In lab <em>Pie Charts, Box Plots, Scatter Plots, and Bubble Plots</em>, we learned how to create a scatter plot and then fit a regression line. It took ~20 lines of code to create the scatter plot along with the regression fit. In this final section, we will explore <em>seaborn</em> and see how efficient it is to create regression lines and fits using this library!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's first install <em>seaborn</em></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># install seaborn</span>
<span class="o">!</span>pip install seaborn

<span class="c1"># import library</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Seaborn installed and imported!&#39;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Create a new dataframe that stores that total number of landed immigrants to Canada per year from 1980 to 2013.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># we can use the sum() method to get the total population per year</span>
<span class="n">df_tot</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">df_can</span><span class="p">[</span><span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span>

<span class="c1"># change the years to type float (useful for regression later on)</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="nb">map</span><span class="p">(</span><span class="nb">float</span><span class="p">,</span><span class="n">df_tot</span><span class="o">.</span><span class="n">index</span><span class="p">)</span>

<span class="c1"># reset the index to put in back in as a column in the df_tot dataframe</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>

<span class="c1"># rename columns</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="s1">&#39;total&#39;</span><span class="p">]</span>

<span class="c1"># view the final dataframe</span>
<span class="n">df_tot</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>With <em>seaborn</em>, generating a regression plot is as simple as calling the <strong>regplot</strong> function.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This is not magic; it is <em>seaborn</em>! You can also customize the color of the scatter plot and regression line. Let's change the color to green.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>You can always customize the marker shape, so instead of circular markers, let's use '+'.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;+&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's blow up the plot a little bit so that it is more appealing to the sight.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;+&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>And let's increase the size of markers so they match the new size of the figure, and add a title and x- and y-labels.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;+&#39;</span><span class="p">,</span> <span class="n">scatter_kws</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;s&#39;</span><span class="p">:</span> <span class="mi">200</span><span class="p">})</span>

<span class="n">ax</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">xlabel</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span> <span class="n">ylabel</span><span class="o">=</span><span class="s1">&#39;Total Immigration&#39;</span><span class="p">)</span> <span class="c1"># add x- and y-labels</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Total Immigration to Canada from 1980 - 2013&#39;</span><span class="p">)</span> <span class="c1"># add title</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>And finally increase the font size of the tickmark labels, the title, and the x- and y-labels so they don't feel left out!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>

<span class="n">sns</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">font_scale</span><span class="o">=</span><span class="mf">1.5</span><span class="p">)</span>

<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;+&#39;</span><span class="p">,</span> <span class="n">scatter_kws</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;s&#39;</span><span class="p">:</span> <span class="mi">200</span><span class="p">})</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">xlabel</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span> <span class="n">ylabel</span><span class="o">=</span><span class="s1">&#39;Total Immigration&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Total Immigration to Canada from 1980 - 2013&#39;</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Amazing! A complete scatter plot with a regression fit with 5 lines of code only. Isn't this really amazing?</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>If you are not a big fan of the purple background, you can easily change the style to a white plain background.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>

<span class="n">sns</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">font_scale</span><span class="o">=</span><span class="mf">1.5</span><span class="p">)</span>
<span class="n">sns</span><span class="o">.</span><span class="n">set_style</span><span class="p">(</span><span class="s1">&#39;ticks&#39;</span><span class="p">)</span> <span class="c1"># change background to white background</span>

<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;+&#39;</span><span class="p">,</span> <span class="n">scatter_kws</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;s&#39;</span><span class="p">:</span> <span class="mi">200</span><span class="p">})</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">xlabel</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span> <span class="n">ylabel</span><span class="o">=</span><span class="s1">&#39;Total Immigration&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Total Immigration to Canada from 1980 - 2013&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Or to a white background with gridlines.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>

<span class="n">sns</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">font_scale</span><span class="o">=</span><span class="mf">1.5</span><span class="p">)</span>
<span class="n">sns</span><span class="o">.</span><span class="n">set_style</span><span class="p">(</span><span class="s1">&#39;whitegrid&#39;</span><span class="p">)</span>

<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_tot</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;+&#39;</span><span class="p">,</span> <span class="n">scatter_kws</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;s&#39;</span><span class="p">:</span> <span class="mi">200</span><span class="p">})</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">xlabel</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span> <span class="n">ylabel</span><span class="o">=</span><span class="s1">&#39;Total Immigration&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Total Immigration to Canada from 1980 - 2013&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: <strong>Use seaborn to create a scatter plot with a regression line to visualize the total immigration from Denmark, Sweden, and Norway to Canada from 1980 to 2013.</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>

<span class="c1"># create df_countries dataframe</span>
<span class="n">df_countries</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;Denmark&#39;</span><span class="p">,</span> <span class="s1">&#39;Norway&#39;</span><span class="p">,</span> <span class="s1">&#39;Sweden&#39;</span><span class="p">],</span> <span class="n">years</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span>

<span class="c1"># create df_total by summing across three countries for each year</span>
<span class="n">df_total</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">df_countries</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>

<span class="c1"># reset index in place</span>
<span class="n">df_total</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># rename columns</span>
<span class="n">df_total</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="s1">&#39;total&#39;</span><span class="p">]</span>

<span class="c1"># change column year from string to int to create scatter plot</span>
<span class="n">df_total</span><span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_total</span><span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">int</span><span class="p">)</span>

<span class="c1"># define figure size</span>
<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">10</span><span class="p">))</span>

<span class="c1"># define background style and font size</span>
<span class="n">sns</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">font_scale</span><span class="o">=</span><span class="mf">1.5</span><span class="p">)</span>
<span class="n">sns</span><span class="o">.</span><span class="n">set_style</span><span class="p">(</span><span class="s1">&#39;whitegrid&#39;</span><span class="p">)</span>

<span class="c1"># generate plot and add title and axes labels</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">regplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;total&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df_total</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;green&#39;</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;+&#39;</span><span class="p">,</span> <span class="n">scatter_kws</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;s&#39;</span><span class="p">:</span> <span class="mi">200</span><span class="p">})</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">xlabel</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span> <span class="n">ylabel</span><span class="o">=</span><span class="s1">&#39;Total Immigration&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Total Immigrationn from Denmark, Sweden, and Norway to Canada from 1980 - 2013&#39;</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span> 
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 align=Left><font size = 5>5. Generating Maps with Python</font></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Introduction">Introduction<a class="anchor-link" href="#Introduction">&#182;</a></h2><p>In this lab, we will learn how to create maps for different objectives. To do that, we will part ways with Matplotlib and work with another Python visualization library, namely <strong>Folium</strong>. What is nice about <strong>Folium</strong> is that it was developed for the sole purpose of visualizing geospatial data. While other libraries are available to visualize geospatial data, such as <strong>plotly</strong>, they might have a cap on how many API calls you can make within a defined time frame. <strong>Folium</strong>, on the other hand, is completely free.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Table-of-Contents">Table of Contents<a class="anchor-link" href="#Table-of-Contents">&#182;</a></h2><div class="alert alert-block alert-info" style="margin-top: 20px">

5.1 Exploring Datasets with *p*andas <br>
5.2 Downloading and Prepping Data <br>
5.3 Introduction to Folium <br>
5.4 Map with Markers <br>
5.5 Choropleth Maps <br>
</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="5.1 Exploring-Datasets-with-pandas-and-Matplotlib">5.1 Exploring Datasets with <em>pandas</em> and Matplotlib<a id="0" /><a class="anchor-link" href="#5.1 Exploring-Datasets-with-pandas-and-Matplotlib">&#182;</a></h2><p>Toolkits: This lab heavily relies on <a href="http://pandas.pydata.org/"><em>pandas</em></a> and <a href="http://www.numpy.org/"><strong>Numpy</strong></a> for data wrangling, analysis, and visualization. The primary plotting library we will explore in this lab is <a href="https://github.com/python-visualization/folium/"><strong>Folium</strong></a>.</p>
<p>Datasets:</p>
<ol>
<li><p>San Francisco Police Department Incidents for the year 2016 - <a href="https://data.sfgov.org/Public-Safety/Police-Department-Incidents-Previous-Year-2016-/ritf-b9ki">Police Department Incidents</a> from San Francisco public data portal. Incidents derived from San Francisco Police Department (SFPD) Crime Incident Reporting system. Updated daily, showing data for the entire year of 2016. Address and location has been anonymized by moving to mid-block or to an intersection.</p>
</li>
<li><p>Immigration to Canada from 1980 to 2013 - <a href="http://www.un.org/en/development/desa/population/migration/data/empirical2/migrationflows.shtml">International migration flows to and from selected countries - The 2015 revision</a> from United Nation's website. The dataset contains annual data on the flows of international migrants as recorded by the countries of destination. The data presents both inflows and outflows according to the place of birth, citizenship or place of previous / next residence both for foreigners and nationals. For this lesson, we will focus on the Canadian Immigration data</p>
</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="5.2 Downloading-and-Prepping-Data-">5.2 Downloading and Prepping Data <a id="2" /><a class="anchor-link" href="#5.2 Downloading-and-Prepping-Data-">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Import Primary Modules:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>  <span class="c1"># useful for many scientific computing in Python</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span> <span class="c1"># primary data structure library</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="5.3 Introduction-to-Folium-">5.3 Introduction to Folium <a id="4" /><a class="anchor-link" href="#5.3 Introduction-to-Folium-">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Folium is a powerful Python library that helps you create several types of Leaflet maps. The fact that the Folium results are interactive makes this library very useful for dashboard building.</p>
<p>From the official Folium documentation page:</p>
<blockquote><p>Folium builds on the data wrangling strengths of the Python ecosystem and the mapping strengths of the Leaflet.js library. Manipulate your data in Python, then visualize it in on a Leaflet map via Folium.</p>
<p>Folium makes it easy to visualize data that's been manipulated in Python on an interactive Leaflet map. It enables both the binding of data to a map for choropleth visualizations as well as passing Vincent/Vega visualizations as markers on the map.</p>
<p>The library has a number of built-in tilesets from OpenStreetMap, Mapbox, and Stamen, and supports custom tilesets with Mapbox or Cloudmade API keys. Folium supports both GeoJSON and TopoJSON overlays, as well as the binding of data to those overlays to create choropleth maps with color-brewer color schemes.</p>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Let's-install-Folium">Let's install <strong>Folium</strong><a class="anchor-link" href="#Let's-install-Folium">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Folium</strong> is not available by default. So, we first need to install it before we are able to import it.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="o">!</span>conda install -c conda-forge <span class="nv">folium</span><span class="o">=</span><span class="m">0</span>.5.0 --yes
<span class="kn">import</span> <span class="nn">folium</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Folium installed and imported!&#39;</span><span class="p">)</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Generating the world map is straigtforward in <strong>Folium</strong>. You simply create a <strong>Folium</strong> <em>Map</em> object and then you display it. What is attactive about <strong>Folium</strong> maps is that they are interactive, so you can zoom into any region of interest despite the initial zoom level.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># define the world map</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">()</span>

<span class="c1"># display world map</span>
<span class="n">world_map</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Go ahead. Try zooming in and out of the rendered map above.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>You can customize this default definition of the world map by specifying the centre of your map and the intial zoom level.</p>
<p>All locations on a map are defined by their respective <em>Latitude</em> and <em>Longitude</em> values. So you can create a map and pass in a center of <em>Latitude</em> and <em>Longitude</em> values of <strong>[0, 0]</strong>.</p>
<p>For a defined center, you can also define the intial zoom level into that location when the map is rendered. <strong>The higher the zoom level the more the map is zoomed into the center</strong>.</p>
<p>Let's create a map centered around Canada and play with the zoom level to see how it affects the rendered map.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># define the world map centered around Canada with a low zoom level</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="mf">56.130</span><span class="p">,</span> <span class="o">-</span><span class="mf">106.35</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>

<span class="c1"># display world map</span>
<span class="n">world_map</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's create the map again with a higher zoom level</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># define the world map centered around Canada with a higher zoom level</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="mf">56.130</span><span class="p">,</span> <span class="o">-</span><span class="mf">106.35</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">8</span><span class="p">)</span>

<span class="c1"># display world map</span>
<span class="n">world_map</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As you can see, the higher the zoom level the more the map is zoomed into the given center.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: Create a map of Mexico with a zoom level of 4.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>
<span class="c1"># Mexico&#39;s geolocation coordinates</span>
<span class="n">mexico_latitude</span> <span class="o">=</span> <span class="mf">23.6345</span> 
<span class="n">mexico_longitude</span> <span class="o">=</span> <span class="o">-</span><span class="mf">102.5528</span>

<span class="c1"># world map centered around Canada with a higher zoom level</span>
<span class="n">mexico_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="n">mexico_latitude</span><span class="p">,</span> <span class="n">mexico_longitude</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>

<span class="n">mexico_map</span>
</pre></div>

 
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Another cool feature of <strong>Folium</strong> is that you can generate different map styles.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="A.-Stamen-Toner-Maps">A. Stamen Toner Maps<a class="anchor-link" href="#A.-Stamen-Toner-Maps">&#182;</a></h3><p>These are high-contrast B+W (black and white) maps. They are perfect for data mashups and exploring river meanders and coastal zones.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's create a Stamen Toner map of canada with a zoom level of 4.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># create a Stamen Toner map of the world centered around Canada</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="mf">56.130</span><span class="p">,</span> <span class="o">-</span><span class="mf">106.35</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span> <span class="n">tiles</span><span class="o">=</span><span class="s1">&#39;Stamen Toner&#39;</span><span class="p">)</span>

<span class="c1"># display map</span>
<span class="n">world_map</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Feel free to zoom in and out to see how this style compares to the default one.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="B.-Stamen-Terrain-Maps">B. Stamen Terrain Maps<a class="anchor-link" href="#B.-Stamen-Terrain-Maps">&#182;</a></h3><p>These are maps that feature hill shading and natural vegetation colors. They showcase advanced labeling and linework generalization of dual-carriageway roads.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's create a Stamen Terrain map of Canada with zoom level 4.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># create a Stamen Toner map of the world centered around Canada</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="mf">56.130</span><span class="p">,</span> <span class="o">-</span><span class="mf">106.35</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span> <span class="n">tiles</span><span class="o">=</span><span class="s1">&#39;Stamen Terrain&#39;</span><span class="p">)</span>

<span class="c1"># display map</span>
<span class="n">world_map</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Feel free to zoom in and out to see how this style compares to Stamen Toner and the default style.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="C.-Mapbox-Bright-Maps">C. Mapbox Bright Maps<a class="anchor-link" href="#C.-Mapbox-Bright-Maps">&#182;</a></h3><p>These are maps that quite similar to the default style, except that the borders are not visible with a low zoom level. Furthermore, unlike the default style where country names are displayed in each country's native language, <em>Mapbox Bright</em> style displays all country names in English.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's create a world map with this style.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># create a world map with a Mapbox Bright style.</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">tiles</span><span class="o">=</span><span class="s1">&#39;Mapbox Bright&#39;</span><span class="p">)</span>

<span class="c1"># display the map</span>
<span class="n">world_map</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Zoom in and notice how the borders start showing as you zoom in, and the displayed country names are in English.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Question</strong>: Create a map of Mexico to visualize its hill shading and natural vegetation. Use a zoom level of 6.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Answer =</span>
<span class="c1"># Mexico&#39;s geolocation coordinates</span>
<span class="n">mexico_latitude</span> <span class="o">=</span> <span class="mf">23.6345</span> 
<span class="n">mexico_longitude</span> <span class="o">=</span> <span class="o">-</span><span class="mf">102.5528</span>

<span class="c1"># world map centered around Canada with a higher zoom level</span>
<span class="n">mexico_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="n">mexico_latitude</span><span class="p">,</span> <span class="n">mexico_longitude</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">6</span><span class="p">,</span> <span class="n">tiles</span><span class="o">=</span><span class="s1">&#39;Stamen Terrain&#39;</span><span class="p">)</span>

<span class="n">mexico_map</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="5.4 Maps-with-Markers-">5.4 Maps with Markers <a id="6" /><a class="anchor-link" href="#5.4 Maps-with-Markers-">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's download and import the data on police department incidents using <em>pandas</em> <code>read_csv()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Download the dataset and read it into a <em>pandas</em> dataframe:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_incidents</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;https://ibm.box.com/shared/static/nmcltjmocdi8sd5tk93uembzdec8zyaq.csv&#39;</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Dataset downloaded and read into a pandas dataframe!&#39;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's take a look at the first five items in our dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_incidents</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>So each row consists of 13 features:</p>
<blockquote><ol>
<li><strong>IncidntNum</strong>: Incident Number</li>
<li><strong>Category</strong>: Category of crime or incident</li>
<li><strong>Descript</strong>: Description of the crime or incident</li>
<li><strong>DayOfWeek</strong>: The day of week on which the incident occurred</li>
<li><strong>Date</strong>: The Date on which the incident occurred</li>
<li><strong>Time</strong>: The time of day on which the incident occurred</li>
<li><strong>PdDistrict</strong>: The police department district</li>
<li><strong>Resolution</strong>: The resolution of the crime in terms whether the perpetrator was arrested or not</li>
<li><strong>Address</strong>: The closest address to where the incident took place</li>
<li><strong>X</strong>: The longitude value of the crime location </li>
<li><strong>Y</strong>: The latitude value of the crime location</li>
<li><strong>Location</strong>: A tuple of the latitude and the longitude values</li>
<li><strong>PdId</strong>: The police department ID</li>
</ol>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's find out how many entries there are in our dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_incidents</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>So the dataframe consists of 150,500 crimes, which took place in the year 2016. In order to reduce computational cost, let's just work with the first 100 incidents in this dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># get the first 100 crimes in the df_incidents dataframe</span>
<span class="n">limit</span> <span class="o">=</span> <span class="mi">100</span>
<span class="n">df_incidents</span> <span class="o">=</span> <span class="n">df_incidents</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="n">limit</span><span class="p">,</span> <span class="p">:]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's confirm that our dataframe now consists only of 100 crimes.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_incidents</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we reduced the data a little bit, let's visualize where these crimes took place in the city of San Francisco. We will use the default style and we will initialize the zoom level to 12.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># San Francisco latitude and longitude values</span>
<span class="n">latitude</span> <span class="o">=</span> <span class="mf">37.77</span>
<span class="n">longitude</span> <span class="o">=</span> <span class="o">-</span><span class="mf">122.42</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># create map and display it</span>
<span class="n">sanfran_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="n">latitude</span><span class="p">,</span> <span class="n">longitude</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span>

<span class="c1"># display the map of San Francisco</span>
<span class="n">sanfran_map</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now let's superimpose the locations of the crimes onto the map. The way to do that in <strong>Folium</strong> is to create a <em>feature group</em> with its own features and style and then add it to the sanfran_map.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># instantiate a feature group for the incidents in the dataframe</span>
<span class="n">incidents</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">map</span><span class="o">.</span><span class="n">FeatureGroup</span><span class="p">()</span>

<span class="c1"># loop through the 100 crimes and add each to the incidents feature group</span>
<span class="k">for</span> <span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">,</span> <span class="ow">in</span> <span class="nb">zip</span><span class="p">(</span><span class="n">df_incidents</span><span class="o">.</span><span class="n">Y</span><span class="p">,</span> <span class="n">df_incidents</span><span class="o">.</span><span class="n">X</span><span class="p">):</span>
    <span class="n">incidents</span><span class="o">.</span><span class="n">add_child</span><span class="p">(</span>
        <span class="n">folium</span><span class="o">.</span><span class="n">features</span><span class="o">.</span><span class="n">CircleMarker</span><span class="p">(</span>
            <span class="p">[</span><span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">],</span>
            <span class="n">radius</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> <span class="c1"># define how big you want the circle markers to be</span>
            <span class="n">color</span><span class="o">=</span><span class="s1">&#39;yellow&#39;</span><span class="p">,</span>
            <span class="n">fill</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
            <span class="n">fill_color</span><span class="o">=</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span>
            <span class="n">fill_opacity</span><span class="o">=</span><span class="mf">0.6</span>
        <span class="p">)</span>
    <span class="p">)</span>

<span class="c1"># add incidents to map</span>
<span class="n">sanfran_map</span><span class="o">.</span><span class="n">add_child</span><span class="p">(</span><span class="n">incidents</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>You can also add some pop-up text that would get displayed when you hover over a marker. Let's make each marker display the category of the crime when hovered over.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># instantiate a feature group for the incidents in the dataframe</span>
<span class="n">incidents</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">map</span><span class="o">.</span><span class="n">FeatureGroup</span><span class="p">()</span>

<span class="c1"># loop through the 100 crimes and add each to the incidents feature group</span>
<span class="k">for</span> <span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">,</span> <span class="ow">in</span> <span class="nb">zip</span><span class="p">(</span><span class="n">df_incidents</span><span class="o">.</span><span class="n">Y</span><span class="p">,</span> <span class="n">df_incidents</span><span class="o">.</span><span class="n">X</span><span class="p">):</span>
    <span class="n">incidents</span><span class="o">.</span><span class="n">add_child</span><span class="p">(</span>
        <span class="n">folium</span><span class="o">.</span><span class="n">features</span><span class="o">.</span><span class="n">CircleMarker</span><span class="p">(</span>
            <span class="p">[</span><span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">],</span>
            <span class="n">radius</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> <span class="c1"># define how big you want the circle markers to be</span>
            <span class="n">color</span><span class="o">=</span><span class="s1">&#39;yellow&#39;</span><span class="p">,</span>
            <span class="n">fill</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
            <span class="n">fill_color</span><span class="o">=</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span>
            <span class="n">fill_opacity</span><span class="o">=</span><span class="mf">0.6</span>
        <span class="p">)</span>
    <span class="p">)</span>

<span class="c1"># add pop-up text to each marker on the map</span>
<span class="n">latitudes</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">df_incidents</span><span class="o">.</span><span class="n">Y</span><span class="p">)</span>
<span class="n">longitudes</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">df_incidents</span><span class="o">.</span><span class="n">X</span><span class="p">)</span>
<span class="n">labels</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">df_incidents</span><span class="o">.</span><span class="n">Category</span><span class="p">)</span>

<span class="k">for</span> <span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">,</span> <span class="n">label</span> <span class="ow">in</span> <span class="nb">zip</span><span class="p">(</span><span class="n">latitudes</span><span class="p">,</span> <span class="n">longitudes</span><span class="p">,</span> <span class="n">labels</span><span class="p">):</span>
    <span class="n">folium</span><span class="o">.</span><span class="n">Marker</span><span class="p">([</span><span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">],</span> <span class="n">popup</span><span class="o">=</span><span class="n">label</span><span class="p">)</span><span class="o">.</span><span class="n">add_to</span><span class="p">(</span><span class="n">sanfran_map</span><span class="p">)</span>    
    
<span class="c1"># add incidents to map</span>
<span class="n">sanfran_map</span><span class="o">.</span><span class="n">add_child</span><span class="p">(</span><span class="n">incidents</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Isn't this really cool? Now you are able to know what crime category occurred at each marker.</p>
<p>If you find the map to be so congested will all these markers, there are two remedies to this problem. The simpler solution is to remove these location markers and just add the text to the circle markers themselves as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># create map and display it</span>
<span class="n">sanfran_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="n">latitude</span><span class="p">,</span> <span class="n">longitude</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span>

<span class="c1"># loop through the 100 crimes and add each to the map</span>
<span class="k">for</span> <span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">,</span> <span class="n">label</span> <span class="ow">in</span> <span class="nb">zip</span><span class="p">(</span><span class="n">df_incidents</span><span class="o">.</span><span class="n">Y</span><span class="p">,</span> <span class="n">df_incidents</span><span class="o">.</span><span class="n">X</span><span class="p">,</span> <span class="n">df_incidents</span><span class="o">.</span><span class="n">Category</span><span class="p">):</span>
    <span class="n">folium</span><span class="o">.</span><span class="n">features</span><span class="o">.</span><span class="n">CircleMarker</span><span class="p">(</span>
        <span class="p">[</span><span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">],</span>
        <span class="n">radius</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> <span class="c1"># define how big you want the circle markers to be</span>
        <span class="n">color</span><span class="o">=</span><span class="s1">&#39;yellow&#39;</span><span class="p">,</span>
        <span class="n">fill</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
        <span class="n">popup</span><span class="o">=</span><span class="n">label</span><span class="p">,</span>
        <span class="n">fill_color</span><span class="o">=</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span>
        <span class="n">fill_opacity</span><span class="o">=</span><span class="mf">0.6</span>
    <span class="p">)</span><span class="o">.</span><span class="n">add_to</span><span class="p">(</span><span class="n">sanfran_map</span><span class="p">)</span>

<span class="c1"># show map</span>
<span class="n">sanfran_map</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The other proper remedy is to group the markers into different clusters. Each cluster is then represented by the number of crimes in each neighborhood. These clusters can be thought of as pockets of San Francisco which you can then analyze separately.</p>
<p>To implement this, we start off by instantiating a <em>MarkerCluster</em> object and adding all the data points in the dataframe to this object.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">folium</span> <span class="k">import</span> <span class="n">plugins</span>

<span class="c1"># let&#39;s start again with a clean copy of the map of San Francisco</span>
<span class="n">sanfran_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span> <span class="o">=</span> <span class="p">[</span><span class="n">latitude</span><span class="p">,</span> <span class="n">longitude</span><span class="p">],</span> <span class="n">zoom_start</span> <span class="o">=</span> <span class="mi">12</span><span class="p">)</span>

<span class="c1"># instantiate a mark cluster object for the incidents in the dataframe</span>
<span class="n">incidents</span> <span class="o">=</span> <span class="n">plugins</span><span class="o">.</span><span class="n">MarkerCluster</span><span class="p">()</span><span class="o">.</span><span class="n">add_to</span><span class="p">(</span><span class="n">sanfran_map</span><span class="p">)</span>

<span class="c1"># loop through the dataframe and add each data point to the mark cluster</span>
<span class="k">for</span> <span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">,</span> <span class="n">label</span><span class="p">,</span> <span class="ow">in</span> <span class="nb">zip</span><span class="p">(</span><span class="n">df_incidents</span><span class="o">.</span><span class="n">Y</span><span class="p">,</span> <span class="n">df_incidents</span><span class="o">.</span><span class="n">X</span><span class="p">,</span> <span class="n">df_incidents</span><span class="o">.</span><span class="n">Category</span><span class="p">):</span>
    <span class="n">folium</span><span class="o">.</span><span class="n">Marker</span><span class="p">(</span>
        <span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="n">lat</span><span class="p">,</span> <span class="n">lng</span><span class="p">],</span>
        <span class="n">icon</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span>
        <span class="n">popup</span><span class="o">=</span><span class="n">label</span><span class="p">,</span>
    <span class="p">)</span><span class="o">.</span><span class="n">add_to</span><span class="p">(</span><span class="n">incidents</span><span class="p">)</span>

<span class="c1"># display map</span>
<span class="n">sanfran_map</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Notice how when you zoom out all the way, all markers are grouped into one cluster, <em>the global cluster</em>, of 100 markers or crimes, which is the total number of crimes in our dataframe. Once you start zooming in, the <em>global cluster</em> will start breaking up into smaller clusters. Zooming in all the way will result in individual markers.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="5.5 Choropleth-Maps-">5.5 Choropleth Maps <a id="8" /><a class="anchor-link" href="#5.5 Choropleth-Maps-">&#182;</a></h2><p>A <code>Choropleth</code> map is a thematic map in which areas are shaded or patterned in proportion to the measurement of the statistical variable being displayed on the map, such as population density or per-capita income. The choropleth map provides an easy way to visualize how a measurement varies across a geographic area or it shows the level of variability within a region. Below is a <code>Choropleth</code> map of the US depicting the population by square mile per state.</p>
<p><img src = "https://ibm.box.com/shared/static/2kzaknzdf6crt3n5rx6haskg3wiaklxl.png" width = 600></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now, let's create our own <code>Choropleth</code> map of the world depicting immigration from various countries to Canada.</p>
<p>Let's first download and import our primary Canadian immigration dataset using <em>pandas</em> <code>read_excel()</code> method. Normally, before we can do that, we would need to download a module which <em>pandas</em> requires to read in excel files. This module is <strong>xlrd</strong>. For your convenience, we have pre-installed this module, so you would not have to worry about that. Otherwise, you would need to run the following line of code to install the <strong>xlrd</strong> module:</p>

<pre><code>!conda install -c anaconda xlrd --yes</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Download the dataset and read it into a <em>pandas</em> dataframe:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_excel</span><span class="p">(</span><span class="s1">&#39;https://ibm.box.com/shared/static/lw190pt9zpy5bd1ptyg2aw15awomz9pu.xlsx&#39;</span><span class="p">,</span>
                     <span class="n">sheet_name</span><span class="o">=</span><span class="s1">&#39;Canada by Citizenship&#39;</span><span class="p">,</span>
                     <span class="n">skiprows</span><span class="o">=</span><span class="nb">range</span><span class="p">(</span><span class="mi">20</span><span class="p">),</span>
                     <span class="n">skip_footer</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Data downloaded and read into a dataframe!&#39;</span><span class="p">)</span>
</pre></div>

  
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's take a look at the first five items in our dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's find out how many entries there are in our dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># print the dimensions of the dataframe</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df_can</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Clean up data. We will make some modifications to the original dataset to make it easier to create our visualizations. Refer to <em>Introduction to Matplotlib and Line Plots</em> and <em>Area Plots, Histograms, and Bar Plots</em> notebooks for a detailed description of this preprocessing.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># clean up the dataset to remove unnecessary columns (eg. REG) </span>
<span class="n">df_can</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;AREA&#39;</span><span class="p">,</span><span class="s1">&#39;REG&#39;</span><span class="p">,</span><span class="s1">&#39;DEV&#39;</span><span class="p">,</span><span class="s1">&#39;Type&#39;</span><span class="p">,</span><span class="s1">&#39;Coverage&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># let&#39;s rename the columns so that they make sense</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;OdName&#39;</span><span class="p">:</span><span class="s1">&#39;Country&#39;</span><span class="p">,</span> <span class="s1">&#39;AreaName&#39;</span><span class="p">:</span><span class="s1">&#39;Continent&#39;</span><span class="p">,</span><span class="s1">&#39;RegName&#39;</span><span class="p">:</span><span class="s1">&#39;Region&#39;</span><span class="p">},</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1"># for sake of consistency, let&#39;s also make all column labels of type string</span>
<span class="n">df_can</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="nb">str</span><span class="p">,</span> <span class="n">df_can</span><span class="o">.</span><span class="n">columns</span><span class="p">))</span>

<span class="c1"># add total column</span>
<span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_can</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="c1"># years that we will be using in this lesson - useful for plotting later on</span>
<span class="n">years</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">map</span><span class="p">(</span><span class="nb">str</span><span class="p">,</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1980</span><span class="p">,</span> <span class="mi">2014</span><span class="p">)))</span>
<span class="nb">print</span> <span class="p">(</span><span class="s1">&#39;data dimensions:&#39;</span><span class="p">,</span> <span class="n">df_can</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>


</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's take a look at the first five items of our cleaned dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_can</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In order to create a <code>Choropleth</code> map, we need a GeoJSON file that defines the areas/boundaries of the state, county, or country that we are interested in. In our case, since we are endeavoring to create a world map, we want a GeoJSON that defines the boundaries of all world countries. For your convenience, we will be providing you with this file, so let's go ahead and download it. Let's name it <strong>world_countries.json</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># download countries geojson file</span>
<span class="o">!</span>wget --quiet https://ibm.box.com/shared/static/cto2qv7nx6yq19logfcissyy4euo8lho.json -O world_countries.json
    
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;GeoJSON file downloaded!&#39;</span><span class="p">)</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we have the GeoJSON file, let's create a world map, centered around <strong>[0, 0]</strong> <em>latitude</em> and <em>longitude</em> values, with an intial zoom level of 2, and using <em>Mapbox Bright</em> style.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">world_geo</span> <span class="o">=</span> <span class="sa">r</span><span class="s1">&#39;world_countries.json&#39;</span> <span class="c1"># geojson file</span>

<span class="c1"># create a plain world map</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span> <span class="n">tiles</span><span class="o">=</span><span class="s1">&#39;Mapbox Bright&#39;</span><span class="p">)</span>

<span class="c1"># generate choropleth map using the total immigration of each country to Canada from 1980 to 2013</span>
<span class="n">world_map</span><span class="o">.</span><span class="n">choropleth</span><span class="p">(</span>
    <span class="n">geo_data</span><span class="o">=</span><span class="n">world_geo</span><span class="p">,</span>
    <span class="n">data</span><span class="o">=</span><span class="n">df_can</span><span class="p">,</span>
    <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Country&#39;</span><span class="p">,</span> <span class="s1">&#39;Total&#39;</span><span class="p">],</span>
    <span class="n">key_on</span><span class="o">=</span><span class="s1">&#39;feature.properties.name&#39;</span><span class="p">,</span>
    <span class="n">fill_color</span><span class="o">=</span><span class="s1">&#39;YlOrRd&#39;</span><span class="p">,</span> 
    <span class="n">fill_opacity</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> 
    <span class="n">line_opacity</span><span class="o">=</span><span class="mf">0.2</span><span class="p">,</span>
    <span class="n">legend_name</span><span class="o">=</span><span class="s1">&#39;Immigration to Canada&#39;</span>
<span class="p">)</span>

<span class="c1"># display map</span>
<span class="n">world_map</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Wow! Very interesting map. As per our <code>Choropleth</code> map legend, the darker the color of a country and the closer the color to red, the higher the number of immigrants from that country. Accordingly, the highest immigration over the course of 33 years (from 1980 to 2013) was from China, India, and the Philippines, followed by Poland, Pakistan, and interestingly, the US.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Notice how the legend is displaying a negative boundary or threshold. Let's fix that by defining our own thresholds and starting with 0 instead of -6,918!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">world_geo</span> <span class="o">=</span> <span class="sa">r</span><span class="s1">&#39;world_countries.json&#39;</span>

<span class="c1"># create a numpy array of length 6 and has linear spacing from the minium total immigration to the maximum total immigration</span>
<span class="n">threshold_scale</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">linspace</span><span class="p">(</span><span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">(),</span>
                              <span class="n">df_can</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">(),</span>
                              <span class="mi">6</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="nb">int</span><span class="p">)</span>
<span class="n">threshold_scale</span> <span class="o">=</span> <span class="n">threshold_scale</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span> <span class="c1"># change the numpy array to a list</span>
<span class="n">threshold_scale</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">=</span> <span class="n">threshold_scale</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">+</span> <span class="mi">1</span> <span class="c1"># make sure that the last value of the list is greater than the maximum immigration</span>

<span class="c1"># let Folium determine the scale.</span>
<span class="n">world_map</span> <span class="o">=</span> <span class="n">folium</span><span class="o">.</span><span class="n">Map</span><span class="p">(</span><span class="n">location</span><span class="o">=</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">],</span> <span class="n">zoom_start</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span> <span class="n">tiles</span><span class="o">=</span><span class="s1">&#39;Mapbox Bright&#39;</span><span class="p">)</span>
<span class="n">world_map</span><span class="o">.</span><span class="n">choropleth</span><span class="p">(</span>
    <span class="n">geo_data</span><span class="o">=</span><span class="n">world_geo</span><span class="p">,</span>
    <span class="n">data</span><span class="o">=</span><span class="n">df_can</span><span class="p">,</span>
    <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Country&#39;</span><span class="p">,</span> <span class="s1">&#39;Total&#39;</span><span class="p">],</span>
    <span class="n">key_on</span><span class="o">=</span><span class="s1">&#39;feature.properties.name&#39;</span><span class="p">,</span>
    <span class="n">threshold_scale</span><span class="o">=</span><span class="n">threshold_scale</span><span class="p">,</span>
    <span class="n">fill_color</span><span class="o">=</span><span class="s1">&#39;YlOrRd&#39;</span><span class="p">,</span> 
    <span class="n">fill_opacity</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> 
    <span class="n">line_opacity</span><span class="o">=</span><span class="mf">0.2</span><span class="p">,</span>
    <span class="n">legend_name</span><span class="o">=</span><span class="s1">&#39;Immigration to Canada&#39;</span><span class="p">,</span>
    <span class="n">reset</span><span class="o">=</span><span class="kc">True</span>
<span class="p">)</span>
<span class="n">world_map</span>
</pre></div>

   
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Much better now! Feel free to play around with the data and perhaps create <code>Choropleth</code> maps for individuals years, or perhaps decades, and see how they compare with the entire period from 1980 to 2013.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This notebook was originally created by <a href="https://www.linkedin.com/in/jayrajasekharan">Jay Rajasekharan</a> with contributions from <a href="https://www.linkedin.com/in/ehsanmkermani">Ehsan M. Kermani</a>, and <a href="https://www.linkedin.com/in/slobodan-markovic">Slobodan Markovic</a>.</p>
<p>This notebook was recently revised by <a href="https://www.linkedin.com/in/aklson/">Alex Aklson</a>. I hope you found this lab session interesting. Feel free to contact me if you have any questions!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This notebook is part of the free course on <strong>Cognitive Class</strong> called <em>Data Visualization with Python</em>. If you accessed this notebook outside the course, you can take this free self-paced course online by clicking <a href="https://cocl.us/DV0101EN_Lab1">here</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Copyright &copy; 2018 <a href="https://cognitiveclass.ai/?utm_source=bducopyrightlink&amp;utm_medium=dswb&amp;utm_campaign=bdu">Cognitive Class</a>. 
This notebook and its source code are released under the terms of the <a href="https://bigdatauniversity.com/mit-license/">MIT License</a>.</p>

</div>
</div>
</div>
    </div>
  </div>
</body>

 


</html>
