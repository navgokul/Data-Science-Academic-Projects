<h1 id="Food-Recipes-Project">Food Recipes Project<a class="anchor-link" href="#Food-Recipes-Project">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Introduction">Introduction<a class="anchor-link" href="#Introduction">&#182;</a></h2><p>The aim of this project is determining the cuisine of a given dish based on its ingredients.The data was compiled by a researcher named Yong-Yeol Ahn, who scraped tens of thousands of food recipes (cuisines and ingredients) from three different websites, namely:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/4fruwan7wmjov3gywiz3swlojw0srv54.png" width="400" /></p>
<p>www.allrecipes.com</p>
<p><img src="https://ibm.box.com/shared/static/cebfdbr22fjxa47lltp0bs533r103g0z.png" width="400" /></p>
<p>www.epicurious.com</p>
<p><img src="https://ibm.box.com/shared/static/epk727njg7xrz49pbkpkzd05cm5ywqmu.png" width="400" /></p>
<p>www.menupan.com</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For more information on Yong-Yeol Ahn and his research, you can read his paper on <a href="http://yongyeol.com/papers/ahn-flavornet-2011.pdf">Flavor Network and the Principles of Food Pairing</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Table-of-Contents">Table of Contents<a class="anchor-link" href="#Table-of-Contents">&#182;</a></h2><div class="alert alert-block alert-info" style="margin-top: 20px">

1. Business Understanding <br>
2. Analytic Approach<br>
3. Data Requirements<br>
4. Data Collection<br>
5. Data Understanding<br>
6. Data Preparation<br>
7. Data Modeling<br>
8. Model Evaluation<br>
</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For more information on Yong-Yeol Ahn and his research, you can read his paper on <a href="http://yongyeol.com/papers/ahn-flavornet-2011.pdf">Flavor Network and the Principles of Food Pairing</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Data-Science-Methodology">Data Science Methodology<a class="anchor-link" href="#Data-Science-Methodology">&#182;</a></h1><p><img src="https://ibm.box.com/shared/static/eyl60n09iige3eo5tac3dweqko2s58oo.png" width="500" /></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Business-Understanding-">Business Understanding <a id="0" /><a class="anchor-link" href="#Business-Understanding-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Business understanding stage important Because it helps clarify the goal of the entity asking the question.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we are interested in automating the process of figuring out the cuisine of a given dish or recipe. Let's apply the business understanding stage to this problem.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Q.-Can-we-predict-the-cuisine-of-a-given-dish-using-the-name-of-the-dish-only?">Q. Can we predict the cuisine of a given dish using the name of the dish only?<a class="anchor-link" href="#Q.-Can-we-predict-the-cuisine-of-a-given-dish-using-the-name-of-the-dish-only?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer = No,<br>
    </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Q.-For-example,-the-following-dish-names-were-taken-from-the-menu-of-a-local-restaurant-in-Toronto,-Ontario-in-Canada.">Q. For example, the following dish names were taken from the menu of a local restaurant in Toronto, Ontario in Canada.<a class="anchor-link" href="#Q.-For-example,-the-following-dish-names-were-taken-from-the-menu-of-a-local-restaurant-in-Toronto,-Ontario-in-Canada.">&#182;</a></h4><h4 id="1.-Beast">1. Beast<a class="anchor-link" href="#1.-Beast">&#182;</a></h4><h4 id="2.-2-PM">2. 2 PM<a class="anchor-link" href="#2.-2-PM">&#182;</a></h4><h4 id="3.-4-Minute">3. 4 Minute<a class="anchor-link" href="#3.-4-Minute">&#182;</a></h4><h4 id="Are-you-able-to-tell-the-cuisine-of-these-dishes?">Are you able to tell the cuisine of these dishes?<a class="anchor-link" href="#Are-you-able-to-tell-the-cuisine-of-these-dishes?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
    Answer = Yes,<br>
    </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Q.-What-about-by-appearance-only?-Yes-or-No.">Q. What about by appearance only? Yes or No.<a class="anchor-link" href="#Q.-What-about-by-appearance-only?-Yes-or-No.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer = No,<br>
</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Q.-What-about-determining-the-cuisine-of-a-dish-based-on-its-ingredients?">Q. What about determining the cuisine of a dish based on its ingredients?<a class="anchor-link" href="#Q.-What-about-determining-the-cuisine-of-a-dish-based-on-its-ingredients?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer = Yes,<br>
</div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As you guessed, yes determining the cuisine of a given dish based on its ingredients seems like a viable solution as some ingredients are unique to cuisines. For example:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li><p>When we talk about <strong>American</strong> cuisines, the first ingredient that comes to one's mind (or at least to my mind =D) is beef or turkey.</p>
</li>
<li><p>When we talk about <strong>British</strong> cuisines, the first ingredient that comes to one's mind is haddock or mint sauce.</p>
</li>
<li><p>When we talk about <strong>Canadian</strong> cuisines, the first ingredient that comes to one's mind is bacon or poutine.</p>
</li>
<li><p>When we talk about <strong>French</strong> cuisines, the first ingredient that comes to one's mind is bread or butter.</p>
</li>
<li><p>When we talk about <strong>Italian</strong> cuisines, the first ingredient that comes to one's mind is tomato or ricotta.</p>
</li>
<li><p>When we talk about <strong>Japanese</strong> cuisines, the first ingredient that comes to one's mind is seaweed or soy sauce.</p>
</li>
<li><p>When we talk about <strong>Chinese</strong> cuisines, the first ingredient that comes to one's mind is ginger or garlic.</p>
</li>
<li><p>When we talk about <strong>indian</strong> cuisines, the first ingredient that comes to one's mind is masala or chillis.</p>
</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Analytic-Approach-">Analytic Approach <a id="2" /><a class="anchor-link" href="#Analytic-Approach-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This step entails expressing the problem in the context of statistical and machine-learning techniques, so that the entity or stakeholders with the problem can identify the most suitable techniques for the desired outcome.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Let's-explore-a-machine-learning-algorithm,-decision-trees,-and-see-if-it-is-the-right-technique-to-automate-the-process-of-identifying-the-cuisine-of-a-given-dish-or-recipe-while-simultaneously-providing-us-with-some-insight-on-why-a-given-recipe-is-believed-to-belong-to-a-certain-type-of-cuisine.">Let's explore a machine learning algorithm, decision trees, and see if it is the right technique to automate the process of identifying the cuisine of a given dish or recipe while simultaneously providing us with some insight on why a given recipe is believed to belong to a certain type of cuisine.<a class="anchor-link" href="#Let's-explore-a-machine-learning-algorithm,-decision-trees,-and-see-if-it-is-the-right-technique-to-automate-the-process-of-identifying-the-cuisine-of-a-given-dish-or-recipe-while-simultaneously-providing-us-with-some-insight-on-why-a-given-recipe-is-believed-to-belong-to-a-certain-type-of-cuisine.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This is a decision tree that a naive person might create manually. Starting at the top with all the recipes for all the cuisines in the world, if a recipe contains <strong>rice</strong>, then this decision tree would classify it as a <strong>Japanese</strong> cuisine. Otherwise, it would be classified as not a <strong>Japanese</strong> cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/1dzmelrcfsgba47rbbagbxiqisqgy63n.png" width="500" /></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Is-this-a-good-decision-tree?--Yes-or--No,-and-why?">Is this a good decision tree?  Yes or  No, and why?<a class="anchor-link" href="#Is-this-a-good-decision-tree?--Yes-or--No,-and-why?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
    Answer = No, because a plethora of dishes from other cuisines contain rice. Therefore, using rice as the ingredient in the Decision node to split on is not a good choice.,<br>
    </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="In-order-to-build-a-very-powerful-decision-tree-for-the-recipe-case-study,-let's-take-some-time-to-learn-more-about-decision-trees.">In order to build a very powerful decision tree for the recipe case study, let's take some time to learn more about decision trees.<a class="anchor-link" href="#In-order-to-build-a-very-powerful-decision-tree-for-the-recipe-case-study,-let's-take-some-time-to-learn-more-about-decision-trees.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li>Decision trees are built using recursive partitioning to classify the data.</li>
<li>When partitioning the data, decision trees use the most predictive feature (ingredient in this case) to split the data.</li>
<li><strong>Predictiveness</strong> is based on decrease in entropy - gain in information, or <em>impurity</em>.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Suppose-that-our-data-is-comprised-of-green-triangles-and-red-circles.">Suppose that our data is comprised of green triangles and red circles.<a class="anchor-link" href="#Suppose-that-our-data-is-comprised-of-green-triangles-and-red-circles.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The following decision tree would be considered the optimal model for classifying the data into a node for green triangles and a node for red circles.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/obwksbsin10mlg2m8x8ehe9xeyjfizqx.png" width="400" /></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Each of the classes in the leaf nodes are completely pure – that is, each leaf node only contains datapoints that belong to the same class.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>On the other hand, the following decision tree is an example of the worst-case scenario that the model could output.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/qenfaznfhwvvvlkjtzjirqgb4j5xx48l.png" width="500" /></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Each leaf node contains datapoints belonging to the two classes resulting in many datapoints ultimately being misclassified.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="A-tree-stops-growing-at-a-node-when:">A tree stops growing at a node when:<a class="anchor-link" href="#A-tree-stops-growing-at-a-node-when:">&#182;</a></h4><ul>
<li>Pure or nearly pure.</li>
<li>No remaining variables on which to further subset the data.</li>
<li>The tree has grown to a preselected size limit.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Here-are-some-characteristics-of-decision-trees:">Here are some characteristics of decision trees:<a class="anchor-link" href="#Here-are-some-characteristics-of-decision-trees:">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/05mkemi191f6hbhw6f3ewrusckkgu861.png" width="800" /></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now let's put what we learned about decision trees to use. Let's try and build a much better version of the decision tree for our recipe problem.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="https://ibm.box.com/shared/static/e1ok280uavy6k8u7loli59ftoz66kk1s.png" width = "500" /></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>I hope you agree that the above decision tree is a much better version than the previous one. Although we are still using <strong>Rice</strong> as the ingredient in the first <em>decision node</em>, recipes get divided into <strong>Asian Food</strong> and <strong>Non-Asian Food</strong>. <strong>Asian Food</strong> is then further divided into <strong>Japanese</strong> and <strong>Not Japanese</strong> based on the <strong>Wasabi</strong> ingredient. This process of splitting <em>leaf nodes</em> continues until each <em>leaf node</em> is pure, i.e., containing recipes belonging to only one cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Accordingly, decision trees is a suitable technique or algorithm for our recipe case study.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Data-Requirements-">Data Requirements <a id="0" /><a class="anchor-link" href="#Data-Requirements-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>we determined that automating the process of determining the cuisine of a given recipe or dish is potentially possible using the ingredients of the recipe or the dish. In order to build a model, we need extensive data of different cuisines and recipes.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Identifying the required data fulfills the data requirements stage of the data science methodology.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This is a decision tree that a naive person might create manually. Starting at the top with all the recipes for all the cuisines in the world, if a recipe contains <strong>rice</strong>, then this decision tree would classify it as a <strong>Japanese</strong> cuisine. Otherwise, it would be classified as not a <strong>Japanese</strong> cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Data-Collection-">Data Collection <a id="0" /><a class="anchor-link" href="#Data-Collection-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>These can be in the form of structured, unstructured, and even semi-structured data relevant to the problem domain.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Web-Scraping-of-Online-Food-Recipes">Web Scraping of Online Food Recipes<a class="anchor-link" href="#Web-Scraping-of-Online-Food-Recipes">&#182;</a></h4><p>A researcher named Yong-Yeol Ahn scraped tens of thousands of food recipes (cuisines and ingredients) from three different websites, namely: www.allrecipes.com, www.epicurious.com, www.menupan.com. we will not need to carry out any data collection as the data that we need to meet the goal defined in the business understanding stage is readily available.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="We-have-data-on-IBM-server.-Let's-download-the-data-and-take-a-look-at-it.">We have data on IBM server. Let's download the data and take a look at it.<a class="anchor-link" href="#We-have-data-on-IBM-server.-Let's-download-the-data-and-take-a-look-at-it.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Using-this-notebook:">Using this notebook:<a class="anchor-link" href="#Using-this-notebook:">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Get the version of Python installed.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># check Python version</span>
<span class="o">!</span>python -V
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Import important modules</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span> <span class="c1"># import library to read data into dataframe</span>
<span class="n">pd</span><span class="o">.</span><span class="n">set_option</span><span class="p">(</span><span class="s1">&#39;display.max_columns&#39;</span><span class="p">,</span> <span class="kc">None</span><span class="p">)</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span> <span class="c1"># import numpy library</span>
<span class="kn">import</span> <span class="nn">re</span><span class="c1"># import library for regular expression</span>
<span class="kn">import</span> <span class="nn">random</span> 
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Read the data from the IBM server into a <em>pandas</em> dataframe</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;https://ibm.box.com/shared/static/5wah9atr5o1akuuavl2z9tkjzdinr1lv.csv&quot;</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Data read into dataframe!&quot;</span><span class="p">)</span> <span class="c1"># takes about 30 seconds</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Show the first few rows.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Get the dimensions of the dataframe.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>So our dataset consists of 57,691 recipes. Each row represents a recipe, and for each recipe, the corresponding cuisine is documented as well as whether 384 ingredients exist in the recipe or not beginning with almond and ending with zucchini.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Data-Understanding-">Data Understanding <a id="2" /><a class="anchor-link" href="#Data-Understanding-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We know that a basic sushi recipe includes the ingredients:</p>
<ul>
<li>rice</li>
<li>soy sauce</li>
<li>wasabi</li>
<li>some fish/vegetables</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's check that these ingredients exist in our dataframe:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ingredients</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">recipes</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>

<span class="nb">print</span><span class="p">([</span><span class="n">match</span><span class="o">.</span><span class="n">group</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span> <span class="k">for</span> <span class="n">ingredient</span> <span class="ow">in</span> <span class="n">ingredients</span> <span class="k">for</span> <span class="n">match</span> <span class="ow">in</span> <span class="p">[(</span><span class="n">re</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="s2">&quot;.*(rice).*&quot;</span><span class="p">))</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">ingredient</span><span class="p">)]</span> <span class="k">if</span> <span class="n">match</span><span class="p">])</span>
<span class="nb">print</span><span class="p">([</span><span class="n">match</span><span class="o">.</span><span class="n">group</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span> <span class="k">for</span> <span class="n">ingredient</span> <span class="ow">in</span> <span class="n">ingredients</span> <span class="k">for</span> <span class="n">match</span> <span class="ow">in</span> <span class="p">[(</span><span class="n">re</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="s2">&quot;.*(wasabi).*&quot;</span><span class="p">))</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">ingredient</span><span class="p">)]</span> <span class="k">if</span> <span class="n">match</span><span class="p">])</span>
<span class="nb">print</span><span class="p">([</span><span class="n">match</span><span class="o">.</span><span class="n">group</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span> <span class="k">for</span> <span class="n">ingredient</span> <span class="ow">in</span> <span class="n">ingredients</span> <span class="k">for</span> <span class="n">match</span> <span class="ow">in</span> <span class="p">[(</span><span class="n">re</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="s2">&quot;.*(soy).*&quot;</span><span class="p">))</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">ingredient</span><span class="p">)]</span> <span class="k">if</span> <span class="n">match</span><span class="p">])</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Yes, they do!</p>
<ul>
<li>rice exists as rice.</li>
<li>wasabi exists as wasabi.</li>
<li>soy exists as soy_sauce.</li>
</ul>
<p>So maybe if a recipe contains all three ingredients: rice, wasabi, and soy_sauce, then we can confidently say that the recipe is a <strong>Japanese</strong> cuisine! Let's keep this in mind!</p>
<hr>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Data-Preparation-">Data Preparation <a id="4" /><a class="anchor-link" href="#Data-Preparation-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This stage involves exploring the data further and making sure that it is in the right format for the machine learning algorithm that we selected in the analytic approach stage, which is decision trees.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>First, look at the data to see if it needs cleaning.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;country&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span> <span class="c1"># frequency table</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>By looking at the above table, we can make the following observations:</p>
<ol>
<li>Cuisine column is labeled as Country, which is inaccurate.</li>
<li>Cuisine names are not consistent as not all of them start with an uppercase first letter.</li>
<li>Some cuisines are duplicated as variation of the country name, such as Vietnam and Vietnamese.</li>
<li>Some cuisines have very few recipes.</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Let's-fixes-these-problems.">Let's fixes these problems.<a class="anchor-link" href="#Let's-fixes-these-problems.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Fix the name of the column showing the cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">column_names</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">values</span>
<span class="n">column_names</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;cuisine&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="n">column_names</span>

<span class="n">recipes</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Make all the cuisine names lowercase.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">lower</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Make the cuisine names consistent.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;austria&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;austrian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;belgium&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;belgian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;china&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;chinese&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;canada&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;canadian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;netherlands&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;dutch&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;france&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;french&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;germany&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;german&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;india&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;indian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;indonesia&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;indonesian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;iran&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;iranian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;italy&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;italian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;japan&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;japanese&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;israel&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;jewish&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;korea&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;korean&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;lebanon&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;lebanese&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;malaysia&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;malaysian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;mexico&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;mexican&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;pakistan&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;pakistani&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;philippines&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;philippine&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;scandinavia&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;scandinavian&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;spain&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;spanish_portuguese&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;portugal&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;spanish_portuguese&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;switzerland&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;swiss&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;thailand&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;thai&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;turkey&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;turkish&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;vietnam&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;vietnamese&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;uk-and-ireland&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;uk-and-irish&quot;</span>
<span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;irish&quot;</span><span class="p">,</span> <span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="s2">&quot;uk-and-irish&quot;</span>

<span class="n">recipes</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># get list of cuisines to keep</span>
<span class="n">recipes_counts</span> <span class="o">=</span> <span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
<span class="n">cuisines_indices</span> <span class="o">=</span> <span class="n">recipes_counts</span> <span class="o">&gt;</span> <span class="mi">50</span>

<span class="n">cuisines_to_keep</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">recipes_counts</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">)[</span><span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">cuisines_indices</span><span class="p">)])</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">rows_before</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="c1"># number of rows of original dataframe</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Number of rows of original dataframe is </span><span class="si">{}</span><span class="s2">.&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">rows_before</span><span class="p">))</span>

<span class="n">recipes</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">recipes</span><span class="p">[</span><span class="s1">&#39;cuisine&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">isin</span><span class="p">(</span><span class="n">cuisines_to_keep</span><span class="p">)]</span>

<span class="n">rows_after</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="c1"># number of rows of processed dataframe</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Number of rows of processed dataframe is </span><span class="si">{}</span><span class="s2">.&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">rows_after</span><span class="p">))</span>

<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">{}</span><span class="s2"> rows removed!&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">rows_before</span> <span class="o">-</span> <span class="n">rows_after</span><span class="p">))</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Convert all Yes's to 1's and the No's to 0's</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">to_replace</span><span class="o">=</span><span class="s2">&quot;Yes&quot;</span><span class="p">,</span> <span class="n">value</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">recipes</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">to_replace</span><span class="o">=</span><span class="s2">&quot;No&quot;</span><span class="p">,</span> <span class="n">value</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Let's-analyze-the-data-a-little-more-in-order-to-learn-the-data-better-and-note-any-interesting-preliminary-observations.">Let's analyze the data a little more in order to learn the data better and note any interesting preliminary observations.<a class="anchor-link" href="#Let's-analyze-the-data-a-little-more-in-order-to-learn-the-data-better-and-note-any-interesting-preliminary-observations.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Run the following cell to get the recipes that contain <strong>rice</strong> <em>and</em> <strong>soy</strong> <em>and</em> <strong>wasabi</strong> <em>and</em> <strong>seaweed</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">check_recipes</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span>
    <span class="p">(</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;rice&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="mi">1</span><span class="p">)</span> <span class="o">&amp;</span>
    <span class="p">(</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;soy_sauce&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="mi">1</span><span class="p">)</span> <span class="o">&amp;</span>
    <span class="p">(</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;wasabi&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="mi">1</span><span class="p">)</span> <span class="o">&amp;</span>
    <span class="p">(</span><span class="n">recipes</span><span class="p">[</span><span class="s2">&quot;seaweed&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="mi">1</span><span class="p">)</span>
<span class="p">]</span>

<span class="n">check_recipes</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Based-on-the-results-of-the-above-code,-can-we-classify-all-recipes-that-contain-rice-and-soy-and-wasabi-and-seaweed-as-Japanese-recipes?-Why?">Based on the results of the above code, can we classify all recipes that contain <strong>rice</strong> <em>and</em> <strong>soy</strong> <em>and</em> <strong>wasabi</strong> <em>and</em> <strong>seaweed</strong> as <strong>Japanese</strong> recipes? Why?<a class="anchor-link" href="#Based-on-the-results-of-the-above-code,-can-we-classify-all-recipes-that-contain-rice-and-soy-and-wasabi-and-seaweed-as-Japanese-recipes?-Why?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer = NO,BECAUSE THIS ingredients ALSO USED IN ASIAN AND EAST_ASIAN COUNTRIES
        </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's count the ingredients across all recipes.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># sum each column</span>
<span class="n">ing</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span> <span class="mi">1</span><span class="p">:]</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># define each column as a pandas series</span>
<span class="n">ingredient</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">ing</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">index</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">ing</span><span class="p">)))</span>
<span class="n">count</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">ing</span><span class="p">),</span> <span class="n">index</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">ing</span><span class="p">)))</span>

<span class="c1"># create the dataframe</span>
<span class="n">ing_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="nb">dict</span><span class="p">(</span><span class="n">ingredient</span> <span class="o">=</span> <span class="n">ingredient</span><span class="p">,</span> <span class="n">count</span> <span class="o">=</span> <span class="n">count</span><span class="p">))</span>
<span class="n">ing_df</span> <span class="o">=</span> <span class="n">ing_df</span><span class="p">[[</span><span class="s2">&quot;ingredient&quot;</span><span class="p">,</span> <span class="s2">&quot;count&quot;</span><span class="p">]]</span>
<span class="nb">print</span><span class="p">(</span><span class="n">ing_df</span><span class="o">.</span><span class="n">to_string</span><span class="p">())</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ing_df</span><span class="o">.</span><span class="n">sort_values</span><span class="p">([</span><span class="s2">&quot;count&quot;</span><span class="p">],</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">ing_df</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">ing_df</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="What-are-the-3-most-popular-ingredients?">What are the 3 most popular ingredients?<a class="anchor-link" href="#What-are-the-3-most-popular-ingredients?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer =
1.EGG 

2.WHEAT

3.BUTTER
    </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>However, note that there is a problem with the above table. There are ~40,000 American recipes in our dataset, which means that the data is biased towards American ingredients.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Therefore</strong>, let's compute a more objective summary of the ingredients by looking at the ingredients per cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Let's-create-a-profile-for-each-cuisine.">Let's create a <em>profile</em> for each cuisine.<a class="anchor-link" href="#Let's-create-a-profile-for-each-cuisine.">&#182;</a></h4><p>In other words, let's try to find out what ingredients Chinese people typically use, and what is <strong>Canadian</strong> food for example.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cuisines</span> <span class="o">=</span> <span class="n">recipes</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s2">&quot;cuisine&quot;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">cuisines</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As shown above, we have just created a dataframe where each row is a cuisine and each column (except for the first column) is an ingredient, and the row values represent the percentage of each ingredient in the corresponding cuisine.</p>
<p><strong>For example</strong>:</p>
<ul>
<li><em>almond</em> is present across 15.65% of all of the <strong>African</strong> recipes.</li>
<li><em>butter</em> is present across 38.11% of all of the <strong>Canadian</strong> recipes.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's print out the profile for each cuisine by displaying the top four ingredients in each cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">num_ingredients</span> <span class="o">=</span> <span class="mi">4</span> <span class="c1"># define number of top ingredients to print</span>

<span class="c1"># define a function that prints the top ingredients for each cuisine</span>
<span class="k">def</span> <span class="nf">print_top_ingredients</span><span class="p">(</span><span class="n">row</span><span class="p">):</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">row</span><span class="o">.</span><span class="n">name</span><span class="o">.</span><span class="n">upper</span><span class="p">())</span>
    <span class="n">row_sorted</span> <span class="o">=</span> <span class="n">row</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span><span class="o">*</span><span class="mi">100</span>
    <span class="n">top_ingredients</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">row_sorted</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">)[</span><span class="mi">0</span><span class="p">:</span><span class="n">num_ingredients</span><span class="p">]</span>
    <span class="n">row_sorted</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">row_sorted</span><span class="p">)[</span><span class="mi">0</span><span class="p">:</span><span class="n">num_ingredients</span><span class="p">]</span>

    <span class="k">for</span> <span class="n">ind</span><span class="p">,</span> <span class="n">ingredient</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">top_ingredients</span><span class="p">):</span>
        <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">%s</span><span class="s2"> (</span><span class="si">%d%%</span><span class="s2">)&quot;</span> <span class="o">%</span> <span class="p">(</span><span class="n">ingredient</span><span class="p">,</span> <span class="n">row_sorted</span><span class="p">[</span><span class="n">ind</span><span class="p">]),</span> <span class="n">end</span><span class="o">=</span><span class="s1">&#39; &#39;</span><span class="p">)</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>

<span class="c1"># apply function to cuisines dataframe</span>
<span class="n">create_cuisines_profiles</span> <span class="o">=</span> <span class="n">cuisines</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">print_top_ingredients</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>At this point, we feel that we have understood the data well and the data is ready and is in the right format for modeling!</p>
<hr>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Data-Modeling-">Data Modeling <a id="2" /><a class="anchor-link" href="#Data-Modeling-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Download and install more libraries and dependies to build decision trees.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># import decision trees scikit-learn libraries</span>
<span class="o">%</span><span class="k">matplotlib</span> inline
<span class="kn">from</span> <span class="nn">sklearn</span> <span class="k">import</span> <span class="n">tree</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">accuracy_score</span><span class="p">,</span> <span class="n">confusion_matrix</span>

<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="kn">import</span> <span class="nn">graphviz</span>

<span class="kn">from</span> <span class="nn">sklearn.tree</span> <span class="k">import</span> <span class="n">export_graphviz</span>

<span class="kn">import</span> <span class="nn">itertools</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">recipes</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="[bamboo_tree]-Only-Asian-and-Indian-Cuisines">[bamboo_tree] Only Asian and Indian Cuisines<a class="anchor-link" href="#[bamboo_tree]-Only-Asian-and-Indian-Cuisines">&#182;</a></h2><p>Here, we are creating a decision tree for the recipes for just some of the Asian (Korean, Japanese, Chinese, Thai) and Indian cuisines. The reason for this is because the decision tree does not run well when the data is biased towards one cuisine, in this case American cuisines. One option is to exclude the American cuisines from our analysis or just build decision trees for different subsets of the data. Let's go with the latter solution.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's build our decision tree using the data pertaining to the Asian and Indian cuisines and name our decision tree <em>bamboo_tree</em>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># select subset of cuisines</span>
<span class="n">asian_indian_recipes</span> <span class="o">=</span> <span class="n">recipes</span><span class="p">[</span><span class="n">recipes</span><span class="o">.</span><span class="n">cuisine</span><span class="o">.</span><span class="n">isin</span><span class="p">([</span><span class="s2">&quot;korean&quot;</span><span class="p">,</span> <span class="s2">&quot;japanese&quot;</span><span class="p">,</span> <span class="s2">&quot;chinese&quot;</span><span class="p">,</span> <span class="s2">&quot;thai&quot;</span><span class="p">,</span> <span class="s2">&quot;indian&quot;</span><span class="p">])]</span>
<span class="n">cuisines</span> <span class="o">=</span> <span class="n">asian_indian_recipes</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span>
<span class="n">ingredients</span> <span class="o">=</span> <span class="n">asian_indian_recipes</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span><span class="mi">1</span><span class="p">:]</span>

<span class="n">bamboo_tree</span> <span class="o">=</span> <span class="n">tree</span><span class="o">.</span><span class="n">DecisionTreeClassifier</span><span class="p">(</span><span class="n">max_depth</span><span class="o">=</span><span class="mi">3</span><span class="p">)</span>
<span class="n">bamboo_tree</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">ingredients</span><span class="p">,</span> <span class="n">cuisines</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Decision tree model saved to bamboo_tree!&quot;</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's plot the decision tree and examine how it looks like.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">export_graphviz</span><span class="p">(</span><span class="n">bamboo_tree</span><span class="p">,</span>
                <span class="n">feature_names</span><span class="o">=</span><span class="nb">list</span><span class="p">(</span><span class="n">ingredients</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">values</span><span class="p">),</span>
                <span class="n">out_file</span><span class="o">=</span><span class="s2">&quot;bamboo_tree.dot&quot;</span><span class="p">,</span>
                <span class="n">class_names</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">unique</span><span class="p">(</span><span class="n">cuisines</span><span class="p">),</span>
                <span class="n">filled</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                <span class="n">node_ids</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                <span class="n">special_characters</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                <span class="n">impurity</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span>
                <span class="n">label</span><span class="o">=</span><span class="s2">&quot;all&quot;</span><span class="p">,</span>
                <span class="n">leaves_parallel</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>

<span class="k">with</span> <span class="nb">open</span><span class="p">(</span><span class="s2">&quot;bamboo_tree.dot&quot;</span><span class="p">)</span> <span class="k">as</span> <span class="n">bamboo_tree_image</span><span class="p">:</span>
    <span class="n">bamboo_tree_graph</span> <span class="o">=</span> <span class="n">bamboo_tree_image</span><span class="o">.</span><span class="n">read</span><span class="p">()</span>
<span class="n">graphviz</span><span class="o">.</span><span class="n">Source</span><span class="p">(</span><span class="n">bamboo_tree_graph</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The decision tree learned:</p>
<ul>
<li>If a recipe contains <em>cumin</em> and <em>fish</em> and <strong>no</strong> <em>yoghurt</em>, then it is most likely a <strong>Thai</strong> recipe.</li>
<li>If a recipe contains <em>cumin</em> but <strong>no</strong> <em>fish</em> and <strong>no</strong> <em>soy_sauce</em>, then it is most likely an <strong>Indian</strong> recipe.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>You can analyze the remaining branches of the tree to come up with similar rules for determining the cuisine of different recipes.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Feel free to select another subset of cuisines and build a decision tree of their recipes. You can select some European cuisines and build a decision tree to explore the ingredients that differentiate them.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Model-Evaluation-">Model Evaluation <a id="4" /><a class="anchor-link" href="#Model-Evaluation-">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To evaluate our model of Asian and Indian cuisines, we will split our dataset into a training set and a test set. We will build the decision tree using the training set. Then, we will test the model on the test set and compare the cuisines that the model predicts to the actual cuisines.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's first create a new dataframe using only the data pertaining to the Asian and the Indian cuisines, and let's call the new dataframe <strong>bamboo</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">bamboo</span> <span class="o">=</span> <span class="n">recipes</span><span class="p">[</span><span class="n">recipes</span><span class="o">.</span><span class="n">cuisine</span><span class="o">.</span><span class="n">isin</span><span class="p">([</span><span class="s2">&quot;korean&quot;</span><span class="p">,</span> <span class="s2">&quot;japanese&quot;</span><span class="p">,</span> <span class="s2">&quot;chinese&quot;</span><span class="p">,</span> <span class="s2">&quot;thai&quot;</span><span class="p">,</span> <span class="s2">&quot;indian&quot;</span><span class="p">])]</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's see how many recipes exist for each cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">bamboo</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's remove 30 recipes from each cuisine to use as the test set, and let's name this test set <strong>bamboo_test</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># set sample size</span>
<span class="n">sample_n</span> <span class="o">=</span> <span class="mi">30</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Create a dataframe containing 30 recipes from each cuisine, selected randomly.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># take 30 recipes from each cuisine</span>
<span class="n">random</span><span class="o">.</span><span class="n">seed</span><span class="p">(</span><span class="mi">1234</span><span class="p">)</span> <span class="c1"># set random seed</span>
<span class="n">bamboo_test</span> <span class="o">=</span> <span class="n">bamboo</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s2">&quot;cuisine&quot;</span><span class="p">,</span> <span class="n">group_keys</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span><span class="o">.</span><span class="n">sample</span><span class="p">(</span><span class="n">sample_n</span><span class="p">))</span>

<span class="n">bamboo_test_ingredients</span> <span class="o">=</span> <span class="n">bamboo_test</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span><span class="mi">1</span><span class="p">:]</span> <span class="c1"># ingredients</span>
<span class="n">bamboo_test_cuisines</span> <span class="o">=</span> <span class="n">bamboo_test</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="c1"># corresponding cuisines or labels</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Check that there are 30 recipes for each cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># check that we have 30 recipes from each cuisine</span>
<span class="n">bamboo_test</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Next, let's create the training set by removing the test set from the <strong>bamboo</strong> dataset, and let's call the training set <strong>bamboo_train</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">bamboo_test_index</span> <span class="o">=</span> <span class="n">bamboo</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">isin</span><span class="p">(</span><span class="n">bamboo_test</span><span class="o">.</span><span class="n">index</span><span class="p">)</span>
<span class="n">bamboo_train</span> <span class="o">=</span> <span class="n">bamboo</span><span class="p">[</span><span class="o">~</span><span class="n">bamboo_test_index</span><span class="p">]</span>

<span class="n">bamboo_train_ingredients</span> <span class="o">=</span> <span class="n">bamboo_train</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span><span class="mi">1</span><span class="p">:]</span> <span class="c1"># ingredients</span>
<span class="n">bamboo_train_cuisines</span> <span class="o">=</span> <span class="n">bamboo_train</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span> <span class="c1"># corresponding cuisines or labels</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Check that there are 30 <em>fewer</em> recipes now for each cuisine.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">bamboo_train</span><span class="p">[</span><span class="s2">&quot;cuisine&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's build the decision tree using the training set, <strong>bamboo_train</strong>, and name the generated tree <strong>bamboo_train_tree</strong> for prediction.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let's plot the decision tree and explore it.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">export_graphviz</span><span class="p">(</span><span class="n">bamboo_train_tree</span><span class="p">,</span>
                <span class="n">feature_names</span><span class="o">=</span><span class="nb">list</span><span class="p">(</span><span class="n">bamboo_train_ingredients</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">values</span><span class="p">),</span>
                <span class="n">out_file</span><span class="o">=</span><span class="s2">&quot;bamboo_train_tree.dot&quot;</span><span class="p">,</span>
                <span class="n">class_names</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">unique</span><span class="p">(</span><span class="n">bamboo_train_cuisines</span><span class="p">),</span>
                <span class="n">filled</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                <span class="n">node_ids</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                <span class="n">special_characters</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                <span class="n">impurity</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span>
                <span class="n">label</span><span class="o">=</span><span class="s2">&quot;all&quot;</span><span class="p">,</span>
                <span class="n">leaves_parallel</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>

<span class="k">with</span> <span class="nb">open</span><span class="p">(</span><span class="s2">&quot;bamboo_train_tree.dot&quot;</span><span class="p">)</span> <span class="k">as</span> <span class="n">bamboo_train_tree_image</span><span class="p">:</span>
    <span class="n">bamboo_train_tree_graph</span> <span class="o">=</span> <span class="n">bamboo_train_tree_image</span><span class="o">.</span><span class="n">read</span><span class="p">()</span>
<span class="n">graphviz</span><span class="o">.</span><span class="n">Source</span><span class="p">(</span><span class="n">bamboo_train_tree_graph</span><span class="p">)</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we defined our tree to be deeper, more decision nodes are generated.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Now-let's-test-our-model-on-the-test-data.">Now let's test our model on the test data.<a class="anchor-link" href="#Now-let's-test-our-model-on-the-test-data.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>bamboo_pred_cuisines = bamboo_train_tree.predict(bamboo_test_ingredients)</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To quantify how well the decision tree is able to determine the cuisine of each recipe correctly, we will create a confusion matrix which presents a nice summary on how many recipes from each cuisine are correctly classified. It also sheds some light on what cuisines are being confused with what other cuisines.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">test_cuisines</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">unique</span><span class="p">(</span><span class="n">bamboo_test_cuisines</span><span class="p">)</span>
<span class="n">bamboo_confusion_matrix</span> <span class="o">=</span> <span class="n">confusion_matrix</span><span class="p">(</span><span class="n">bamboo_test_cuisines</span><span class="p">,</span> <span class="n">bamboo_pred_cuisines</span><span class="p">,</span> <span class="n">test_cuisines</span><span class="p">)</span>
<span class="n">title</span> <span class="o">=</span> <span class="s1">&#39;Bamboo Confusion Matrix&#39;</span>
<span class="n">cmap</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">cm</span><span class="o">.</span><span class="n">Blues</span>

<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">8</span><span class="p">,</span> <span class="mi">6</span><span class="p">))</span>
<span class="n">bamboo_confusion_matrix</span> <span class="o">=</span> <span class="p">(</span>
    <span class="n">bamboo_confusion_matrix</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;float&#39;</span><span class="p">)</span> <span class="o">/</span> <span class="n">bamboo_confusion_matrix</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)[:,</span> <span class="n">np</span><span class="o">.</span><span class="n">newaxis</span><span class="p">]</span>
    <span class="p">)</span> <span class="o">*</span> <span class="mi">100</span>

<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">bamboo_confusion_matrix</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;nearest&#39;</span><span class="p">,</span> <span class="n">cmap</span><span class="o">=</span><span class="n">cmap</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="n">title</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">colorbar</span><span class="p">()</span>
<span class="n">tick_marks</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">test_cuisines</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="n">tick_marks</span><span class="p">,</span> <span class="n">test_cuisines</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">yticks</span><span class="p">(</span><span class="n">tick_marks</span><span class="p">,</span> <span class="n">test_cuisines</span><span class="p">)</span>

<span class="n">fmt</span> <span class="o">=</span> <span class="s1">&#39;.2f&#39;</span>
<span class="n">thresh</span> <span class="o">=</span> <span class="n">bamboo_confusion_matrix</span><span class="o">.</span><span class="n">max</span><span class="p">()</span> <span class="o">/</span> <span class="mf">2.</span>
<span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">j</span> <span class="ow">in</span> <span class="n">itertools</span><span class="o">.</span><span class="n">product</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="n">bamboo_confusion_matrix</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span> <span class="nb">range</span><span class="p">(</span><span class="n">bamboo_confusion_matrix</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">1</span><span class="p">])):</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">text</span><span class="p">(</span><span class="n">j</span><span class="p">,</span> <span class="n">i</span><span class="p">,</span> <span class="nb">format</span><span class="p">(</span><span class="n">bamboo_confusion_matrix</span><span class="p">[</span><span class="n">i</span><span class="p">,</span> <span class="n">j</span><span class="p">],</span> <span class="n">fmt</span><span class="p">),</span>
             <span class="n">horizontalalignment</span><span class="o">=</span><span class="s2">&quot;center&quot;</span><span class="p">,</span>
             <span class="n">color</span><span class="o">=</span><span class="s2">&quot;white&quot;</span> <span class="k">if</span> <span class="n">bamboo_confusion_matrix</span><span class="p">[</span><span class="n">i</span><span class="p">,</span> <span class="n">j</span><span class="p">]</span> <span class="o">&gt;</span> <span class="n">thresh</span> <span class="k">else</span> <span class="s2">&quot;black&quot;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">tight_layout</span><span class="p">()</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;True label&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Predicted label&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The rows represent the actual cuisines from the dataset and the columns represent the predicted ones. Each row should sum to 100%. According to this confusion matrix, we make the following observations:</p>
<ul>
<li><p>Using the first row in the confusion matrix, 60% of the <strong>Chinese</strong> recipes in <strong>bamboo_test</strong> were correctly classified by our decision tree whereas 37% of the <strong>Chinese</strong> recipes were misclassified as <strong>Korean</strong> and 3% were misclassified as <strong>Indian</strong>.</p>
</li>
<li><p>Using the Indian row, 77% of the <strong>Indian</strong> recipes in <strong>bamboo_test</strong> were correctly classified by our decision tree and 3% of the <strong>Indian</strong> recipes were misclassified as <strong>Chinese</strong> and 13% were misclassified as <strong>Korean</strong> and 7% were misclassified as <strong>Thai</strong>.</p>
</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Please note</strong> that because decision trees are created using random sampling of the datapoints in the training set, then you may not get the same results every time you create the decision tree even using the same training set. The performance should still be comparable though! So don't worry if you get slightly different numbers in your confusion matrix than the ones shown above.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Using-the-reference-confusion-matrix,-how-many-Japanese-recipes-were-correctly-classified-by-our-decision-tree?">Using the reference confusion matrix, how many <strong>Japanese</strong> recipes were correctly classified by our decision tree?<a class="anchor-link" href="#Using-the-reference-confusion-matrix,-how-many-Japanese-recipes-were-correctly-classified-by-our-decision-tree?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer = 36.67
    </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Also-using-the-reference-confusion-matrix,-how-many-Korean-recipes-were-misclassified-as-Japanese?">Also using the reference confusion matrix, how many <strong>Korean</strong> recipes were misclassified as <strong>Japanese</strong>?<a class="anchor-link" href="#Also-using-the-reference-confusion-matrix,-how-many-Korean-recipes-were-misclassified-as-Japanese?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer = 3.33%
    </div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="What-cuisine-has-the-least-number-of-recipes-correctly-classified-by-the-decision-tree-using-the-reference-confusion-matrix?">What cuisine has the least number of recipes correctly classified by the decision tree using the reference confusion matrix?<a class="anchor-link" href="#What-cuisine-has-the-least-number-of-recipes-correctly-classified-by-the-decision-tree-using-the-reference-confusion-matrix?">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div class="alert alert-block alert-info" style="margin-top: 20px">
Answer = Japanese cuisine, with 36.67% only
    </div>
</div>
</div>
</div>
    </div>
  </div>
</body>

 


</html>
