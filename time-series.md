<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="Brief indroduction to Time Series analysis.">
<meta name="keywords" content="ARIMAARMAMoving averageSMASMMAEWMAETS decomposition,  ">
<title>Time Series Analysis | Wajid Manzoor</title>
<link rel="stylesheet" href="css/syntax.css">

<link rel="stylesheet" type="text/css" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
<!--<link rel="stylesheet" type="text/css" href="css/bootstrap.min.css">-->
<link rel="stylesheet" href="css/modern-business.css">
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<link rel="stylesheet" href="css/customstyles.css">
<link rel="stylesheet" href="css/boxshadowproperties.css">
<!-- most color styles are extracted out to here -->
<link rel="stylesheet" href="css/theme-blue.css">

<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-cookie/1.4.1/jquery.cookie.min.js"></script>
<script src="js/jquery.navgoco.min.js"></script>


<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
<!-- Anchor.js -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/anchor-js/4.2.0/anchor.min.js"></script>
<script src="js/toc.js"></script>
<script src="js/customscripts.js"></script>

<link rel="shortcut icon" href="images/favicon.ico">

<!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries -->
<!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
<!--[if lt IE 9]>
<script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
<script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
<![endif]-->

<link rel="alternate" type="application/rss+xml" title="wajidmanzoor.github.io" href="/feed.xml">

<script type="text/javascript" async 
src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?
config=TeX-AMS-MML_HTMLorMML"></script>
    <script>
        $(document).ready(function() {
            // Initialize navgoco with default options
            $("#mysidebar").navgoco({
                caretHtml: '',
                accordion: true,
                openClass: 'active', // open
                save: false, // leave false or nav highlighting doesn't work right
                cookie: {
                    name: 'navgoco',
                    expires: false,
                    path: '/'
                },
                slide: {
                    duration: 400,
                    easing: 'swing'
                }
            });

            $("#collapseAll").click(function(e) {
                e.preventDefault();
                $("#mysidebar").navgoco('toggle', false);
            });

            $("#expandAll").click(function(e) {
                e.preventDefault();
                $("#mysidebar").navgoco('toggle', true);
            });

        });

    </script>
    <script>
        $(function () {
            $('[data-toggle="tooltip"]').tooltip()
        })
    </script>
    <script>
        $(document).ready(function() {
            $("#tg-sb-link").click(function() {
                $("#tg-sb-sidebar").toggle();
                $("#tg-sb-content").toggleClass('col-md-9');
                $("#tg-sb-content").toggleClass('col-md-12');
                $("#tg-sb-icon").toggleClass('fa-toggle-on');
                $("#tg-sb-icon").toggleClass('fa-toggle-off');
            });
        });
    </script>
    

</head>
<body>
<!-- Navigation -->
<nav class="navbar navbar-inverse navbar-static-top">
    <div class="container topnavlinks">
        <div class="navbar-header">
            <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
                <span class="sr-only">Toggle navigation</span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
            </button>
            <a class="fa fa-home fa-lg navbar-brand" href="/">&nbsp;<span class="projectTitle"> Wajid Manzoor</span></a>
        </div>
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
            <ul class="nav navbar-nav navbar-right">
                <!-- toggle sidebar button -->
                <li><a id="tg-sb-link" href="#"><i id="tg-sb-icon" class="fa fa-toggle-on"></i> Nav</a></li>
                <!-- entries without drop-downs appear here -->




                
                
                
                <li><a href="https://github.com/wajidmanzoor/wajidmanzoor.github.io" target="_blank" rel="noopener">GitHub</a></li>
                
                
                
                <li><a href="about">About</a></li>
                
                
                
                <!-- entries with drop-downs appear here -->
                <!-- conditional logic to control which topnav appears for the audience defined in the configuration file.-->
                
                
			<li>



  <a class="email" title="Submit feedback" href="#" onclick="javascript:window.location='mailto:wajid.manzoor.1999@gmail.com?subject=Wajid Manzoor feedback&body=I have some feedback about the Time Series Analysis page: ' + window.location.href;"><i class="fa fa-envelope-o"></i> Feedback</a>

</li>

		
                <!--comment out this block if you want to hide search-->
                <li>
                    <!--start search-->
                    <div id="search-demo-container">
                        <input type="text" id="search-input" placeholder="search...">
                        <ul id="results-container"></ul>
                    </div>
                    <script src="js/jekyll-search.js" type="text/javascript"></script>
                    <script type="text/javascript">
                            SimpleJekyllSearch.init({
                                searchInput: document.getElementById('search-input'),
                                resultsContainer: document.getElementById('results-container'),
                                dataSource: 'search.json',
                                searchResultTemplate: '<li><a href="{url}" title="Time Series Analysis">{title}</a></li>',
                    noResultsText: 'No results found.',
                            limit: 10,
                            fuzzy: true,
                    })
                    </script>
                    <!--end search-->
                </li>
            </ul>
        </div>
        </div>
        <!-- /.container -->
</nav>

<!-- Page Content -->
<div class="container">
  <div id="main">
    <!-- Content Row -->
    <div class="row">
        
        
            <!-- Sidebar Column -->
            <div class="col-md-3" id="tg-sb-sidebar">
                

<ul id="mysidebar" class="nav">
  <li class="sidebarTitle">Navigation Bar </li>
  
  
  
      
  
  <li>
      <a title="Financial Analysis" href="#">Financial Analysis</a>
      <ul>
          
          
          
          <li><a title="Time Series" href="time-series">Time Series</a></li>
          
          
          
          
      </ul>
   </li>
     
      
      
      <!-- if you aren't using the accordion, uncomment this block:
         <p class="external">
             <a href="#" id="collapseAll">Collapse All</a> | <a href="#" id="expandAll">Expand All</a>
         </p>
         -->
</ul>

<!-- this highlights the active parent class in the navgoco sidebar. this is critical so that the parent expands when you're viewing a page. This must appear below the sidebar code above. Otherwise, if placed inside customscripts.js, the script runs before the sidebar code runs and the class never gets inserted.-->
<script>$("li.active").parents('li').toggleClass("active");</script>

            </div>
            
        

        <!-- Content Column -->
        <div class="col-md-9" id="tg-sb-content">
            <div class="post-header">
   <h1 class="post-title-main">Time Series Analysis</h1>
</div>



<div class="post-content">

   
    <div class="summary">Brief indroduction to Time Series analysis.</div>
   

    
    
<!-- this handles the automatic toc. use ## for subheads to auto-generate the on-page minitoc. if you use html tags, you must supply an ID for the heading element in order for it to appear in the minitoc. -->
<script>
$( document ).ready(function() {
  // Handler for .ready() called.

$('#toc').toc({ minimumHeaders: 0, listType: 'ul', showSpeed: 0, headers: 'h2,h3,h4' });

/* this offset helps account for the space taken up by the floating toolbar. */
$('#toc').on('click', 'a', function() {
  var target = $(this.getAttribute('href'))
    , scroll_target = target.offset().top

  $(window).scrollTop(scroll_target - 10);
  return false
})
  
});
</script>

<div id="toc"></div>

    


    

   <h1 id="introduction">Introduction</h1>

<p>Time series is a discreate sequence taken at  successive spaced points at time.Time series analysis comprises methods for analyzing time series data in order to extract meaningful statistics and other characteristics of the data. Time series forecasting is the use of a model to predict future values based on previously observed values.In this notebook we are going to analysise time series using diffrent techniques to build intuitions and then use those intutions to predict future values of time series using forecasting.Time series forcasting can be done by many model.In this notebook we are going to use ARIMA models.</p>

<h1 id="introduction-to-time-series-with-pandas">Introduction to Time Series with Pandas</h1>
<ul>
  <li>Time series is a panda dataframe with index of datatype datetime</li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="kn">import</span> <span class="nn">datetime</span> <span class="k">as</span> <span class="n">dt</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="n">plt</span>
<span class="kn">from</span> <span class="nn">matplotlib</span> <span class="kn">import</span> <span class="n">style</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="n">pd</span>
<span class="kn">import</span> <span class="nn">pandas_datareader.data</span> <span class="k">as</span> <span class="n">web</span>
<span class="kn">from</span> <span class="nn">datetime</span> <span class="kn">import</span> <span class="n">datetime</span>
<span class="o">%</span><span class="n">matplotlib</span> <span class="n">notebook</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s">"walmart_stock.csv"</span><span class="p">,</span><span class="n">index_col</span><span class="o">=</span><span class="s">'Date'</span><span class="p">,</span><span class="n">parse_dates</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">info</span><span class="p">()</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;class 'pandas.core.frame.DataFrame'&gt;
DatetimeIndex: 1258 entries, 2012-01-03 to 2016-12-30
Data columns (total 6 columns):
Open         1258 non-null float64
High         1258 non-null float64
Low          1258 non-null float64
Close        1258 non-null float64
Volume       1258 non-null int64
Adj Close    1258 non-null float64
dtypes: float64(5), int64(1)
memory usage: 68.8 KB
</code></pre></div></div>

<h2 id="rolling-and-expanding">Rolling and Expanding</h2>
<ul>
  <li>Rolling provides a window to do calculation over a specific datetime period.</li>
  <li>Expanding does the same exact thing as rolling just taking in account every data point from begining to data point of this instant.</li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">8</span><span class="p">)</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-01-03</td>
      <td>59.970001</td>
      <td>61.060001</td>
      <td>59.869999</td>
      <td>60.330002</td>
      <td>12668800</td>
      <td>52.619235</td>
    </tr>
    <tr>
      <td>2012-01-04</td>
      <td>60.209999</td>
      <td>60.349998</td>
      <td>59.470001</td>
      <td>59.709999</td>
      <td>9593300</td>
      <td>52.078475</td>
    </tr>
    <tr>
      <td>2012-01-05</td>
      <td>59.349998</td>
      <td>59.619999</td>
      <td>58.369999</td>
      <td>59.419998</td>
      <td>12768200</td>
      <td>51.825539</td>
    </tr>
    <tr>
      <td>2012-01-06</td>
      <td>59.419998</td>
      <td>59.450001</td>
      <td>58.869999</td>
      <td>59.000000</td>
      <td>8069400</td>
      <td>51.459220</td>
    </tr>
    <tr>
      <td>2012-01-09</td>
      <td>59.029999</td>
      <td>59.549999</td>
      <td>58.919998</td>
      <td>59.180000</td>
      <td>6679300</td>
      <td>51.616215</td>
    </tr>
    <tr>
      <td>2012-01-10</td>
      <td>59.430000</td>
      <td>59.709999</td>
      <td>58.980000</td>
      <td>59.040001</td>
      <td>6907300</td>
      <td>51.494109</td>
    </tr>
    <tr>
      <td>2012-01-11</td>
      <td>59.060001</td>
      <td>59.529999</td>
      <td>59.040001</td>
      <td>59.400002</td>
      <td>6365600</td>
      <td>51.808098</td>
    </tr>
    <tr>
      <td>2012-01-12</td>
      <td>59.790001</td>
      <td>60.000000</td>
      <td>59.400002</td>
      <td>59.500000</td>
      <td>7236400</td>
      <td>51.895316</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">rolling</span><span class="p">(</span><span class="n">window</span><span class="o">=</span><span class="mi">7</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">8</span><span class="p">)</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-01-03</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2012-01-04</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2012-01-05</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2012-01-06</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2012-01-09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2012-01-10</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2012-01-11</td>
      <td>59.495714</td>
      <td>59.895714</td>
      <td>59.074285</td>
      <td>59.440000</td>
      <td>9.007414e+06</td>
      <td>51.842984</td>
    </tr>
    <tr>
      <td>2012-01-12</td>
      <td>59.469999</td>
      <td>59.744285</td>
      <td>59.007143</td>
      <td>59.321429</td>
      <td>8.231357e+06</td>
      <td>51.739567</td>
    </tr>
  </tbody>
</table>
</div>

<ul>
  <li>Here first 7 entries are Nan objects as the data required to calculate the mean over 7 previous data entries was not available</li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">expanding</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">8</span><span class="p">)</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-01-03</td>
      <td>59.970001</td>
      <td>61.060001</td>
      <td>59.869999</td>
      <td>60.330002</td>
      <td>1.266880e+07</td>
      <td>52.619235</td>
    </tr>
    <tr>
      <td>2012-01-04</td>
      <td>60.090000</td>
      <td>60.704999</td>
      <td>59.670000</td>
      <td>60.020001</td>
      <td>1.113105e+07</td>
      <td>52.348855</td>
    </tr>
    <tr>
      <td>2012-01-05</td>
      <td>59.843333</td>
      <td>60.343333</td>
      <td>59.236666</td>
      <td>59.820000</td>
      <td>1.167677e+07</td>
      <td>52.174416</td>
    </tr>
    <tr>
      <td>2012-01-06</td>
      <td>59.737499</td>
      <td>60.120000</td>
      <td>59.145000</td>
      <td>59.615000</td>
      <td>1.077492e+07</td>
      <td>51.995617</td>
    </tr>
    <tr>
      <td>2012-01-09</td>
      <td>59.595999</td>
      <td>60.006000</td>
      <td>59.099999</td>
      <td>59.528000</td>
      <td>9.955800e+06</td>
      <td>51.919737</td>
    </tr>
    <tr>
      <td>2012-01-10</td>
      <td>59.568332</td>
      <td>59.956666</td>
      <td>59.079999</td>
      <td>59.446667</td>
      <td>9.447717e+06</td>
      <td>51.848799</td>
    </tr>
    <tr>
      <td>2012-01-11</td>
      <td>59.495714</td>
      <td>59.895714</td>
      <td>59.074285</td>
      <td>59.440000</td>
      <td>9.007414e+06</td>
      <td>51.842984</td>
    </tr>
    <tr>
      <td>2012-01-12</td>
      <td>59.532500</td>
      <td>59.908749</td>
      <td>59.115000</td>
      <td>59.447500</td>
      <td>8.786038e+06</td>
      <td>51.849526</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">()</span>
<span class="n">df</span><span class="p">[</span><span class="s">"Close"</span><span class="p">]</span><span class="o">=</span><span class="n">data</span><span class="p">[</span><span class="s">'Close'</span><span class="p">]</span>
<span class="n">df</span><span class="p">[</span><span class="s">'Close_rolling_90'</span><span class="p">]</span><span class="o">=</span><span class="n">data</span><span class="p">[</span><span class="s">'Close'</span><span class="p">]</span><span class="o">.</span><span class="n">rolling</span><span class="p">(</span><span class="mi">30</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">df</span><span class="p">[</span><span class="s">"Close_expanding"</span><span class="p">]</span><span class="o">=</span><span class="n">data</span><span class="p">[</span><span class="s">'Close'</span><span class="p">]</span><span class="o">.</span><span class="n">expanding</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">8</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d4395aa90&gt;
</code></pre></div></div>

<p><img src="output_12_1.png" alt="\time-series-data\png" /></p>

<h2 id="resamplling">Resamplling</h2>
<p>It is a Convenience method for frequency conversion and resampling of time series
<strong>Time series offest strings</strong></p>

<table border="1" class="docutils">
<colgroup>
<col width="13%" />
<col width="87%" />
</colgroup>
<thead valign="bottom">
<tr class="row-odd"><th class="head">Alias</th>
<th class="head">Description</th>
</tr>
</thead>
<tbody valign="top">
<tr class="row-even"><td>B</td>
<td>business day frequency</td>
</tr>
<tr class="row-odd"><td>C</td>
<td>custom business day frequency (experimental)</td>
</tr>
<tr class="row-even"><td>D</td>
<td>calendar day frequency</td>
</tr>
<tr class="row-odd"><td>W</td>
<td>weekly frequency</td>
</tr>
<tr class="row-even"><td>M</td>
<td>month end frequency</td>
</tr>
<tr class="row-odd"><td>SM</td>
<td>semi-month end frequency (15th and end of month)</td>
</tr>
<tr class="row-even"><td>BM</td>
<td>business month end frequency</td>
</tr>
<tr class="row-odd"><td>CBM</td>
<td>custom business month end frequency</td>
</tr>
<tr class="row-even"><td>MS</td>
<td>month start frequency</td>
</tr>
<tr class="row-odd"><td>SMS</td>
<td>semi-month start frequency (1st and 15th)</td>
</tr>
<tr class="row-even"><td>BMS</td>
<td>business month start frequency</td>
</tr>
<tr class="row-odd"><td>CBMS</td>
<td>custom business month start frequency</td>
</tr>
<tr class="row-even"><td>Q</td>
<td>quarter end frequency</td>
</tr>
<tr class="row-odd"><td>BQ</td>
<td>business quarter endfrequency</td>
</tr>
<tr class="row-even"><td>QS</td>
<td>quarter start frequency</td>
</tr>
<tr class="row-odd"><td>BQS</td>
<td>business quarter start frequency</td>
</tr>
<tr class="row-even"><td>A</td>
<td>year end frequency</td>
</tr>
<tr class="row-odd"><td>BA</td>
<td>business year end frequency</td>
</tr>
<tr class="row-even"><td>AS</td>
<td>year start frequency</td>
</tr>
<tr class="row-odd"><td>BAS</td>
<td>business year start frequency</td>
</tr>
<tr class="row-even"><td>BH</td>
<td>business hour frequency</td>
</tr>
<tr class="row-odd"><td>H</td>
<td>hourly frequency</td>
</tr>
<tr class="row-even"><td>T, min</td>
<td>minutely frequency</td>
</tr>
<tr class="row-odd"><td>S</td>
<td>secondly frequency</td>
</tr>
<tr class="row-even"><td>L, ms</td>
<td>milliseconds</td>
</tr>
<tr class="row-odd"><td>U, us</td>
<td>microseconds</td>
</tr>
<tr class="row-even"><td>N</td>
<td>nanoseconds</td>
</tr>
</tbody>
</table>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">resample</span><span class="p">(</span><span class="n">rule</span><span class="o">=</span><span class="s">"BA"</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-12-31</td>
      <td>67.158680</td>
      <td>67.602120</td>
      <td>66.786520</td>
      <td>67.215120</td>
      <td>9.239015e+06</td>
      <td>59.389349</td>
    </tr>
    <tr>
      <td>2013-12-31</td>
      <td>75.264048</td>
      <td>75.729405</td>
      <td>74.843055</td>
      <td>75.320516</td>
      <td>6.951496e+06</td>
      <td>68.147179</td>
    </tr>
    <tr>
      <td>2014-12-31</td>
      <td>77.274524</td>
      <td>77.740040</td>
      <td>76.864405</td>
      <td>77.327381</td>
      <td>6.515612e+06</td>
      <td>71.709712</td>
    </tr>
    <tr>
      <td>2015-12-31</td>
      <td>72.569405</td>
      <td>73.064167</td>
      <td>72.034802</td>
      <td>72.491111</td>
      <td>9.040769e+06</td>
      <td>68.831426</td>
    </tr>
    <tr>
      <td>2016-12-30</td>
      <td>69.481349</td>
      <td>70.019643</td>
      <td>69.023492</td>
      <td>69.547063</td>
      <td>9.371645e+06</td>
      <td>68.054229</td>
    </tr>
  </tbody>
</table>
</div>

<ul>
  <li>We can also use custom functions to resample</li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="k">def</span> <span class="nf">first_day</span><span class="p">(</span><span class="n">entry</span><span class="p">):</span>
    <span class="s">"""" Returns first entry on the samplling period"""</span>
    <span class="k">return</span> <span class="n">entry</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">resample</span><span class="p">(</span><span class="n">rule</span><span class="o">=</span><span class="s">"A"</span><span class="p">)</span><span class="o">.</span><span class="nb">apply</span><span class="p">(</span><span class="n">first_day</span><span class="p">)</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-12-31</td>
      <td>59.970001</td>
      <td>61.060001</td>
      <td>59.869999</td>
      <td>60.330002</td>
      <td>12668800</td>
      <td>52.619235</td>
    </tr>
    <tr>
      <td>2013-12-31</td>
      <td>68.930000</td>
      <td>69.239998</td>
      <td>68.449997</td>
      <td>69.239998</td>
      <td>10390800</td>
      <td>61.879708</td>
    </tr>
    <tr>
      <td>2014-12-31</td>
      <td>78.720001</td>
      <td>79.470001</td>
      <td>78.500000</td>
      <td>78.910004</td>
      <td>6878000</td>
      <td>72.254228</td>
    </tr>
    <tr>
      <td>2015-12-31</td>
      <td>86.269997</td>
      <td>86.720001</td>
      <td>85.550003</td>
      <td>85.900002</td>
      <td>4501800</td>
      <td>80.624861</td>
    </tr>
    <tr>
      <td>2016-12-31</td>
      <td>60.500000</td>
      <td>61.490002</td>
      <td>60.360001</td>
      <td>61.459999</td>
      <td>11989200</td>
      <td>59.289713</td>
    </tr>
  </tbody>
</table>
</div>

<h2 id="time-shifting">Time Shifting</h2>
<p>shifts the column of a data frame by any desired interval of time</p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-01-03</td>
      <td>59.970001</td>
      <td>61.060001</td>
      <td>59.869999</td>
      <td>60.330002</td>
      <td>12668800</td>
      <td>52.619235</td>
    </tr>
    <tr>
      <td>2012-01-04</td>
      <td>60.209999</td>
      <td>60.349998</td>
      <td>59.470001</td>
      <td>59.709999</td>
      <td>9593300</td>
      <td>52.078475</td>
    </tr>
    <tr>
      <td>2012-01-05</td>
      <td>59.349998</td>
      <td>59.619999</td>
      <td>58.369999</td>
      <td>59.419998</td>
      <td>12768200</td>
      <td>51.825539</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-01-03</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2012-01-04</td>
      <td>59.970001</td>
      <td>61.060001</td>
      <td>59.869999</td>
      <td>60.330002</td>
      <td>12668800.0</td>
      <td>52.619235</td>
    </tr>
    <tr>
      <td>2012-01-05</td>
      <td>60.209999</td>
      <td>60.349998</td>
      <td>59.470001</td>
      <td>59.709999</td>
      <td>9593300.0</td>
      <td>52.078475</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">tail</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2016-12-28</td>
      <td>69.209999</td>
      <td>69.519997</td>
      <td>69.120003</td>
      <td>69.260002</td>
      <td>4298400.0</td>
      <td>68.754456</td>
    </tr>
    <tr>
      <td>2016-12-29</td>
      <td>69.120003</td>
      <td>69.430000</td>
      <td>68.830002</td>
      <td>69.120003</td>
      <td>6889500.0</td>
      <td>68.615479</td>
    </tr>
    <tr>
      <td>2016-12-30</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">data</span><span class="o">.</span><span class="n">tshift</span><span class="p">(</span><span class="n">periods</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span><span class="n">freq</span><span class="o">=</span><span class="s">"M"</span><span class="p">)</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2012-01-31</td>
      <td>59.970001</td>
      <td>61.060001</td>
      <td>59.869999</td>
      <td>60.330002</td>
      <td>12668800</td>
      <td>52.619235</td>
    </tr>
    <tr>
      <td>2012-01-31</td>
      <td>60.209999</td>
      <td>60.349998</td>
      <td>59.470001</td>
      <td>59.709999</td>
      <td>9593300</td>
      <td>52.078475</td>
    </tr>
    <tr>
      <td>2012-01-31</td>
      <td>59.349998</td>
      <td>59.619999</td>
      <td>58.369999</td>
      <td>59.419998</td>
      <td>12768200</td>
      <td>51.825539</td>
    </tr>
  </tbody>
</table>
</div>

<h1 id="time-series-analysis">Time Series Analysis</h1>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="kn">import</span> <span class="nn">statsmodels.api</span> <span class="k">as</span> <span class="n">sm</span>
</code></pre></div></div>

<h2 id="hodrickprescott-filter">Hodrick–Prescott filter</h2>
<ul>
  <li>Data-smoothing technique used in macroeconimics commonly applied to remove short term fluctuations.</li>
  <li>In practice, it is used to smooth and detrend the Conference Board’s Help Wanted Index so it can be benchmarked against the Bureau of Labor Statistic’s JOLTS, which measures job vacancies in the U.S.</li>
  <li>Let \(y_t\) denote the algorithms of time series variable,then it compromises of trend component \(\tau_t\) ,cynical component \(\zeta_t\) and error component \(\epsilon_t\) such that \(y_t = \tau_t +\zeta_t + \epsilon_t\).Given a positive value \(\lambda\) the trend trend\(\tau_t\) is given by minimizing the quadratic loss function</li>
</ul>

<script type="math/tex; mode=display">\min \bigg\{ \Sigma{(y_t-\tau_t)^2}+\lambda  \Sigma \big[(\tau_{t+1}-\tau_t)-(\tau_t-\tau{t-1})\big]^2\bigg\}</script>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span> <span class="o">=</span> <span class="n">sm</span><span class="o">.</span><span class="n">datasets</span><span class="o">.</span><span class="n">macrodata</span><span class="o">.</span><span class="n">load_pandas</span><span class="p">()</span><span class="o">.</span><span class="n">data</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="k">print</span><span class="p">(</span><span class="n">sm</span><span class="o">.</span><span class="n">datasets</span><span class="o">.</span><span class="n">macrodata</span><span class="o">.</span><span class="n">NOTE</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>::
    Number of Observations - 203

    Number of Variables - 14

    Variable name definitions::

        year      - 1959q1 - 2009q3
        quarter   - 1-4
        realgdp   - Real gross domestic product (Bil. of chained 2005 US\\),
                    seasonally adjusted annual rate)
        realcons  - Real personal consumption expenditures (Bil. of chained
                    2005 US\\), seasonally adjusted annual rate)
        realinv   - Real gross private domestic investment (Bil. of chained
                    2005 US\\), seasonally adjusted annual rate)
        realgovt  - Real federal consumption expenditures &amp; gross investment
                    (Bil. of chained 2005 US\\), seasonally adjusted annual rate)
        realdpi   - Real private disposable income (Bil. of chained 2005
                    US\\), seasonally adjusted annual rate)
        cpi       - End of the quarter consumer price index for all urban
                    consumers: all items (1982-84 = 100, seasonally adjusted).
        m1        - End of the quarter M1 nominal money stock (Seasonally
                    adjusted)
        tbilrate  - Quarterly monthly average of the monthly 3-month
                    treasury bill: secondary market rate
        unemp     - Seasonally adjusted unemployment rate (%)
        pop       - End of the quarter total population: all ages incl. armed
                    forces over seas
        infl      - Inflation rate (ln(cpi_{t}/cpi_{t-1}) * 400)
        realint   - Real interest rate (tbilrate - infl)
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>quarter</th>
      <th>realgdp</th>
      <th>realcons</th>
      <th>realinv</th>
      <th>realgovt</th>
      <th>realdpi</th>
      <th>cpi</th>
      <th>m1</th>
      <th>tbilrate</th>
      <th>unemp</th>
      <th>pop</th>
      <th>infl</th>
      <th>realint</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1959.0</td>
      <td>1.0</td>
      <td>2710.349</td>
      <td>1707.4</td>
      <td>286.898</td>
      <td>470.045</td>
      <td>1886.9</td>
      <td>28.98</td>
      <td>139.7</td>
      <td>2.82</td>
      <td>5.8</td>
      <td>177.146</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1959.0</td>
      <td>2.0</td>
      <td>2778.801</td>
      <td>1733.7</td>
      <td>310.859</td>
      <td>481.301</td>
      <td>1919.7</td>
      <td>29.15</td>
      <td>141.7</td>
      <td>3.08</td>
      <td>5.1</td>
      <td>177.830</td>
      <td>2.34</td>
      <td>0.74</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1959.0</td>
      <td>3.0</td>
      <td>2775.488</td>
      <td>1751.8</td>
      <td>289.226</td>
      <td>491.260</td>
      <td>1916.4</td>
      <td>29.35</td>
      <td>140.5</td>
      <td>3.82</td>
      <td>5.3</td>
      <td>178.657</td>
      <td>2.74</td>
      <td>1.09</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1959.0</td>
      <td>4.0</td>
      <td>2785.204</td>
      <td>1753.7</td>
      <td>299.356</td>
      <td>484.052</td>
      <td>1931.3</td>
      <td>29.37</td>
      <td>140.0</td>
      <td>4.33</td>
      <td>5.6</td>
      <td>179.386</td>
      <td>0.27</td>
      <td>4.06</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1960.0</td>
      <td>1.0</td>
      <td>2847.699</td>
      <td>1770.5</td>
      <td>331.722</td>
      <td>462.199</td>
      <td>1955.5</td>
      <td>29.54</td>
      <td>139.6</td>
      <td>3.50</td>
      <td>5.2</td>
      <td>180.007</td>
      <td>2.31</td>
      <td>1.19</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="c1">#create a sm datetime index that includes year and quater
</span><span class="n">index</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Index</span><span class="p">(</span><span class="n">sm</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">datetools</span><span class="o">.</span><span class="n">dates_from_range</span><span class="p">(</span><span class="s">'1959Q1'</span><span class="p">,</span> <span class="s">'2009Q3'</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="o">.</span><span class="n">index</span><span class="o">=</span><span class="n">index</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">gdp_cycle</span><span class="p">,</span> <span class="n">gdp_trend</span> <span class="o">=</span> <span class="n">sm</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">filters</span><span class="o">.</span><span class="n">hpfilter</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">realgdp</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="p">[</span><span class="s">'trend'</span><span class="p">]</span><span class="o">=</span><span class="n">gdp_trend</span>
<span class="n">df</span><span class="p">[</span><span class="s">'cynical'</span><span class="p">]</span><span class="o">=</span><span class="n">gdp_cycle</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="p">[[</span><span class="s">'realgdp'</span><span class="p">,</span><span class="s">'trend'</span><span class="p">,</span><span class="s">'cynical'</span><span class="p">]]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">6</span><span class="p">));</span>
</code></pre></div></div>

<p><img src="output_34_0.png" alt="\time-series-data\png" /></p>

<p><strong>Disadvantages</strong></p>
<ul>
  <li>If one-time permanent shocks or split growth rates occur, the filter will generate shifts in the trend that do not actually exist.</li>
  <li>Analysis is purely historical and static (closed domain). The filter causes misleading predictions when used dynamically.</li>
  <li>There’s a better alternative. A regression of the variable at date t+h on the four most recent values as of date t offers a robust approach to detrending that achieves all the objectives sought by users of the HP filter with none of its drawbacks.</li>
</ul>

<h2 id="moving-average">Moving Average</h2>
<ul>
  <li>average price over at specific time period</li>
  <li>cuts down the noise on price chart to give the basic idea of which way price is moving</li>
  <li>can act as Support or Resistance</li>
  <li>N or Moving average lenght should be picked according to  trade</li>
  <li>Short N  benifits Short-Term Trades while Longer N to Long-term Trades</li>
  <li>Shorter the N shorter will be the Lag</li>
  <li>Lag is the time taken for MA to signal a potential reversal</li>
</ul>

<h3 id="1-simple-moving-average">1. Simple Moving Average</h3>
<p><script type="math/tex">\text{SMA}_i = \frac{\Sigma x_i}{N}</script>
<script type="math/tex">N = \text{Calculation period}</script></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="p">[</span><span class="s">'SMA6'</span><span class="p">]</span><span class="o">=</span><span class="n">df</span><span class="p">[</span><span class="s">'realgdp'</span><span class="p">]</span><span class="o">.</span><span class="n">rolling</span><span class="p">(</span><span class="n">window</span><span class="o">=</span><span class="mi">6</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">df</span><span class="p">[</span><span class="s">'SMA12'</span><span class="p">]</span><span class="o">=</span><span class="n">df</span><span class="p">[</span><span class="s">'realgdp'</span><span class="p">]</span><span class="o">.</span><span class="n">rolling</span><span class="p">(</span><span class="n">window</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>

<span class="n">df</span><span class="p">[[</span><span class="s">"SMA6"</span><span class="p">,</span><span class="s">'SMA12'</span><span class="p">,</span><span class="s">'realgdp'</span><span class="p">]]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">6</span><span class="p">));</span>
</code></pre></div></div>

<p><img src="output_38_0.png" alt="\time-series-data\png" /></p>

<h3 id="2--smoothed-moving-average-smma">2.  Smoothed Moving Average (SMMA)</h3>
<ul>
  <li>First Value is calculated by 
<script type="math/tex">\text{SMMA}_1 = \frac{\Sigma x_i}{N}</script></li>
  <li>Second Value is calculated by 
<script type="math/tex">\text{SMMA}_2 = \frac{\text{SMMA}_1 \times (N-1) + x_i}{N}</script></li>
  <li>Succeeding Values are calculated by 
<script type="math/tex">\text{SMMA}_i = \frac{\text{SMMA}_{(i-1)} \times N +x_i}{N}</script>
<script type="math/tex">N = \text{Calculation period}</script></li>
</ul>

<h3 id="3-linear-weighted-moving-average">3. LInear Weighted Moving Average</h3>
<p><script type="math/tex">\text{LWMA}_i =\frac{\Sigma x_i \times \omega_i}{\Sigma N}</script>
where \(N =\) Calculation period</p>

<h3 id="4-exponential-weighted-moving-average">4. Exponential weighted moving Average</h3>
<ul>
  <li>An exponential moving average (EMA), also known as an exponentially weighted moving average (EWMA), is a first-order infinite impulse response filter that applies weighting factors which decrease exponentially. The weighting for each older datum decreases exponentially.</li>
</ul>

<p><script type="math/tex">% <![CDATA[
y_t=\begin{cases}x_1 & t=1\\ \alpha x_t+(1-\alpha)y_{t-1} & t>1\end{cases} %]]></script>
\(y_1\) can be intailize to \(x_1\) or average of first 4 or 5 observations. \(y_1\) initailizing effects on resultant moving average if depends on \(\omega\).Smaller \(\omega\) make choice of \(y_1\) relatively more important.</p>

<p>\(y_t = y_{t-1} + \alpha(x_t-y_{t-1})\)</p>

<p>After repeated application of this formula:
\(y_t=\alpha[x_t+(1-\alpha)x_{t-1}+(1-\alpha)^2x_{t-2}+(1-\alpha)^3x_{t-3}+……]\)</p>

<p>\(\frac{1}{\alpha}=1+(1-\alpha)^2+(1-\alpha)^3+(1-\alpha)^4+….\)</p>

<p>so
<script type="math/tex">y_t= \frac{[x_t+(1-\alpha)x_{t-1}+(1-\alpha)^2x_{t-2}+(1-\alpha)^3x_{t-3}+......]}{1+(1-\alpha)^2+(1-\alpha)^3+(1-\alpha)^4+....}</script></p>

<p>taking \(\omega^i=(1-\alpha)^i\) we have
<script type="math/tex">y_t= \frac{\sum_{i=0}^t\omega_i x_{t-1}}{\sum \omega_i}</script></p>

<p>Commonly used values of  \(\alpha\):</p>

<ul>
  <li>
    <p>\(\alpha = \frac{2}{N_{SMA}+1}\)
  This is recomended on the basis that at this value center of mass of an SMA and EMA are equal.</p>

    <p>Proof:</p>

    <p>Let weights of N-days SMA have center of mass at \(R^{th}\) day,where</p>

    <p>\(R_{SMA} = \frac{N+1}{2}\)</p>

    <p>Considering one-based indexing</p>

    <p>Now center of EMA is</p>

    <p>\(R_{EMA}=\alpha[1+2(1-\alpha)+3(1-\alpha)+4(1-\alpha)+…+k(1-\alpha)]\)</p>

    <p>or</p>

    <p>\(R_{EMA}=\alpha\sum_{k=1}^{\infty}k(1-\alpha)^{k-1}\)</p>

    <p>Now as per Maclaurin series we have</p>

    <p>\(\frac{1}{1-x}=\sum_{k=0}^\infty x^k\)</p>

    <p>Taking derivatives we have</p>

    <p>\( (x-1)^{-2} =\sum_{k=0}^\infty kx^{k-1}\)</p>

    <p>\( (x-1)^{-2} =0+\sum_{k=1}^\infty kx^{k-1}\)</p>

    <p>Substituting \(x=1-\alpha \), we get</p>

    <p>\(R_{EMA}=\alpha^{-1}\)</p>

    <p>Now</p>

    <p>\(R_{EMA} = R_{SMA}\)</p>

    <p>\( \alpha^{-1}=\frac{N_{SMA}+1}{2}\)</p>

    <p>\( \alpha = \frac{2}{N_{SMA}+1}\)</p>
  </li>
  <li>
    <p>The defined value of \(\omega \) depends on parameters provided to <code class="language-plaintext highlighter-rouge">.ewm()</code> method</p>
    <ul>
      <li>If <code class="language-plaintext highlighter-rouge">adjust = False</code> then</li>
    </ul>

    <p><script type="math/tex">% <![CDATA[
\omega_i=\begin{cases}\alpha(1-\alpha)^i & i<t\\ (1-\alpha)^i & i=t\end{cases} %]]></script></p>
    <ul>
      <li>if <code class="language-plaintext highlighter-rouge">adjust =True</code> then</li>
    </ul>

    <script type="math/tex; mode=display">% <![CDATA[
\alpha=\begin{cases}\frac{2}{s+1} & \text{for } s\geq 1\\ \frac{1}{1+c} & \text{for } c\geq 0 \\1-e^\frac{\log{0.5}}{h}& \text{for } h>0 \end{cases} %]]></script>

    <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>   * Span (S) corresponds to what is commonly called an "N-day EW moving average".
   * Center of mass (c)
    
   * Half life or h is the period of time for exponential series to reduce to half.
</code></pre></div>    </div>
  </li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="p">[</span><span class="s">"EWMA12"</span><span class="p">]</span><span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s">'realgdp'</span><span class="p">]</span><span class="o">.</span><span class="n">ewm</span><span class="p">(</span><span class="n">span</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">df</span><span class="p">[</span><span class="s">"EWMA24"</span><span class="p">]</span><span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s">'realgdp'</span><span class="p">]</span><span class="o">.</span><span class="n">ewm</span><span class="p">(</span><span class="n">span</span><span class="o">=</span><span class="mi">24</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
<span class="n">df</span><span class="p">[</span><span class="s">"EWMA"</span><span class="p">]</span><span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s">'realgdp'</span><span class="p">]</span><span class="o">.</span><span class="n">ewm</span><span class="p">(</span><span class="n">adjust</span><span class="o">=</span><span class="bp">False</span><span class="p">,</span><span class="n">span</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df</span><span class="p">[[</span><span class="s">'EWMA12'</span><span class="p">,</span><span class="s">'EWMA24'</span><span class="p">,</span><span class="s">'EWMA'</span><span class="p">,</span><span class="s">'SMA6'</span><span class="p">,</span><span class="s">'SMA12'</span><span class="p">,</span><span class="s">'realgdp'</span><span class="p">]][</span><span class="nb">len</span><span class="p">(</span><span class="n">df</span><span class="p">)</span><span class="o">//</span><span class="mi">10</span><span class="p">:]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d37a055d0&gt;
</code></pre></div></div>

<p><img src="output_43_1.png" alt="\time-series-data\png" /></p>

<h2 id="ets-decomposition">ETS-Decomposition</h2>
<ul>
  <li>Decomposition Based on rate of change.</li>
</ul>

<p>It is a seasonal adjusment technique to construct a number of construct series ,which can be reconstructed to orginal by addition or multiplication.The series is usualy decomposed into</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>* \\(\tau_t\\) Trend conponent which reflects the long term progression.
* \\(\zeta_t\\) Cynical component which reflects repeated but not periodic fluctuations.
* \\(S_t\\) Seasonal component reflects seasonality.
* \\(\epsilon_t\\) noise or error reflects random influences.
</code></pre></div></div>

<p><strong>Note: Cynical and trend is grouped into one called just trend in some ETS-decomposition models eg. STL</strong>
Let \(y_t\) be a time series then</p>
<ul>
  <li>For additive model
    <ul>
      <li>Used when trend is linear and seasonality is constant over time</li>
    </ul>
  </li>
</ul>

<script type="math/tex; mode=display">y_t=\tau_t+\zeta_t+S_t+\epsilon_t</script>

<ul>
  <li>For multiplicative model
    <ul>
      <li>Used when trend is non-linear.
<script type="math/tex">y_t=\tau_t\times \zeta_t \times S_t\times \epsilon_t</script></li>
    </ul>
  </li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">airline</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s">'airline_passengers.csv'</span><span class="p">,</span><span class="n">index_col</span><span class="o">=</span><span class="s">"Month"</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="c1"># Get data in correct format
</span><span class="n">airline</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">airline</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">to_datetime</span><span class="p">(</span><span class="n">airline</span><span class="o">.</span><span class="n">index</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="kn">from</span> <span class="nn">statsmodels.tsa.seasonal</span> <span class="kn">import</span> <span class="n">seasonal_decompose</span>
<span class="n">result</span> <span class="o">=</span> <span class="n">seasonal_decompose</span><span class="p">(</span><span class="n">airline</span><span class="p">[</span><span class="s">'Thousands of Passengers'</span><span class="p">],</span> <span class="n">model</span><span class="o">=</span><span class="s">'additive'</span><span class="p">)</span>
<span class="n">fig</span><span class="o">=</span><span class="n">result</span><span class="o">.</span><span class="n">plot</span><span class="p">()</span>
</code></pre></div></div>

<p><img src="output_47_0.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">result</span> <span class="o">=</span> <span class="n">seasonal_decompose</span><span class="p">(</span><span class="n">airline</span><span class="p">[</span><span class="s">'Thousands of Passengers'</span><span class="p">],</span> <span class="n">model</span><span class="o">=</span><span class="s">'multiplicative'</span><span class="p">)</span>
<span class="n">fig</span><span class="o">=</span><span class="n">result</span><span class="o">.</span><span class="n">plot</span><span class="p">()</span>
</code></pre></div></div>

<p><img src="output_48_0.png" alt="\time-series-data\png" /></p>

<p>Some terms before we go ahead</p>

<p><strong>1.Mean</strong>
is average value of the dataset.
<script type="math/tex">\mu=\frac{\sum_0^n x_i}{n}</script>
<strong>2.Variance</strong>
is the expectation of the squared deviation of a random variable from its mean.
<script type="math/tex">\sigma^2=\frac{\sum_0^n (x_i-\mu)^2}{n}</script>
<strong>3.Covariance</strong>
is a measure of the joint variability of two random variables.
<script type="math/tex">\text{cov}(x,y)=\frac{\sum_0^n(x_i-\mu_x)(y_i-\mu_y)}{n}</script>
<strong>4. Stationary series</strong>
is time series whose mean ,variance and covariance are not function of time.</p>

<p><strong>5.Diffrencing</strong>
in statistics is a transformation applied to time-series data in order to make it stationary.</p>

<p>First order diffrencing</p>

<p>\(y’<em>t=y_t-y</em>{t-1}\)</p>

<p>Second order diffrencing</p>

<p>\(y’‘<em>t=y’_t-y’</em>{t-1}\)</p>

<p>and so on</p>

<p>Seasonal diffrencing</p>

<p>\(y’<em>t=y_t-y</em>{t-m}\)</p>

<p>\(m= \) duration of season</p>

<p><strong>6.AutoCorrelation</strong>
 is the similarity between observations as a function of the time lag between them.</p>

<script type="math/tex; mode=display">cor(y_t,y_{t-k})=\frac{cov(y_t,y_{t-k})}{\sigma_{y_t} \sigma_{y_{t-k}}}</script>

<h2 id="ar-model">AR Model</h2>
<p><strong>Autoregressive model</strong>
 specifies that output value depends linearly on its own previous values and on a stochstic term.</p>

<p>Let \(y_t\) be a time series then  \(AR(p)\) AR model of order p is defined as</p>

<script type="math/tex; mode=display">y_t=c+\varphi_1 y_{t-1}+\varphi_2 y_{t-2}+.....+\varphi_p y_{t-p}+\epsilon_t</script>

<p>where \(\varphi_i\) is parameter of model,\(c\) is constant, \(\epsilon_t \) is white noise or error and \(p\) or order reffers to number of lagged terms.</p>

<p>In discreate time series <em>White noise</em> is a sequence of serially uncorrelated random variables with zero mean and finite variance.</p>

<p>using summation we have</p>

<script type="math/tex; mode=display">y_t=c+\sum_{i=1}^p \varphi_iy_{t-i}+\epsilon_t</script>

<p>applying lag operator \(L\) (where \(L^ny_t=y_{t-n})\) we have</p>

<script type="math/tex; mode=display">y_t(1-\varphi_1L-\varphi_2L^2-....-\varphi_pL^p)=\epsilon_t</script>

<script type="math/tex; mode=display">\varphi(L)y_t=\epsilon_t</script>

<p>where \(\varphi(L)y_t\) is polynomail function of \(y_t\).</p>

<p>stationary in \(AR(p)\) model is guarented only if the root of polynomail \((1-\varphi z)=0\) are greater than 1 in absolute value.</p>

<p>if \(\lambda\) is its root then condition is</p>

<table>
  <tbody>
    <tr>
      <td>\(</td>
      <td>\lambda</td>
      <td>=\frac{1}{</td>
      <td>\varphi</td>
      <td>}&gt;1\)</td>
    </tr>
  </tbody>
</table>

<table>
  <tbody>
    <tr>
      <td>\(</td>
      <td>\varphi</td>
      <td>&lt;1\)</td>
    </tr>
  </tbody>
</table>

<p>A necessary but not sufficient requirement for the AR(p) model to be stationary is that
the summation of the p autoregressive coefficients should be less than 1:</p>

<script type="math/tex; mode=display">% <![CDATA[
\sum_{i=0}^p\varphi<1 %]]></script>

<p>Properties of \(AR(1)\):</p>

<ul>
  <li>
    <p>Mean</p>

    <script type="math/tex; mode=display">% <![CDATA[
\begin{align} &\text{we have}\\ &y_t=c+\varphi y_{t-1} + \epsilon_t\\\\ &\text{so}\\ &E(y_t)=E(c) + E(\varphi y_{t-1})+E(\epsilon_t)\\ &E(y_t)=E(c) + \varphi E( y_{t-1})+E(\epsilon_t)\\\\ &\text{for stationary data } E(y_t)=E(y_{t-1})\\ &\text{put } E(y_t)=E(y_{t-1})=\mu_y  \text{and} E(\epsilon_t)=\mu_\epsilon\\ &\mu_y=E(c) + \varphi \mu_y+\mu_\epsilon\\ &\mu_y=\frac{c}{1-\mu_\epsilon}\\\\ &\text{where } E(c) =c \text{ as c is constant}\\ \end{align} %]]></script>
  </li>
  <li>
    <p>Variance</p>

    <script type="math/tex; mode=display">% <![CDATA[
\begin{align}
  &\sigma_y =E(y_t^2)-E(y_t)^2 \\
   &E(y_t^2) = E([c+\varphi y_{t-1}+ \epsilon_t][c+\varphi y_{t-1}+ \epsilon_t]) \\
   &E(y_t^2) = E(c^2)+E(\varphi^2 y_{t-1}^2)+E( \epsilon_t^2)+2E(c \varphi y_{t-1})+2E(c \epsilon_t)+2E( \varphi y_{t-1}  \epsilon_t)\\
   &E(y_t^2) = c^2 + \varphi^2E(y_{t-1}^2)+E( \epsilon_t^2)+2c\varphi E(y_{t-1})+2c E(\epsilon_t)+2\varphi E(  y_{t-1}  \epsilon_t)\\\\
  &\text{substitute } E(x^2)=\sigma_x^2 - \mu_x^2 and E(X)=\mu_x\\
   &\sigma_y^2 - \mu_y^2 =c^2+ \varphi^2(\sigma_y^2 - \mu_y^2)+\sigma_\epsilon^2 - \mu_\epsilon^2+2c\varphi \mu_y+2c \mu_\epsilon+2E( \varphi y_{t-1}  \epsilon_t)\\
  & E(y_t{t-1}\epsilon_t)=0 \text{ coz } \epsilon_t \text{ is random data and its corelation with any  data will be zero }\\\\
   &\sigma_y^2 - \mu_y^2 =c^2+ \varphi^2(\sigma_y^2 - \mu_y^2)+\sigma_\epsilon^2 - \mu_\epsilon^2+2c\varphi \mu_y+2c \mu_\epsilon\\
   &\epsilon_t \text{in discreate stastics has } \mu_\epsilon =0\\\\ 
   &\sigma_y^2-\mu_y^2 =c^2+ \varphi^2(\sigma_y^2-\mu_y^2)+\sigma_\epsilon^2+2c\varphi \mu_y\\
   &\text{as we know }\\
   &\mu_y=\frac{c}{1-\mu_\epsilon}\\
   &\text{as } \mu_\epsilon=0 \text{ so } \mu_y=c\\\\
   &\sigma_y^2-c^2 =c^2+ \varphi^2(\sigma_y^2-c^2)+\sigma_\epsilon^2+2c^2\varphi\\
   &\sigma_y^2 = \frac{c^2[2-\varphi^2+2\varphi]+\sigma_\epsilon^2}{1-\varphi^2}\\
  \end{align} %]]></script>
  </li>
  <li>
    <p>Covariance
  <script type="math/tex">% <![CDATA[
\begin{align}
  &\text{we know}\\
  &cov(a,b)=E\{[a-E(a)][b-E(b)]\}\\\\
  &\text{so}\\
  &cov(y_t,y_{t-1})=E\{[y_t-E(y_t)][y_{t-1}-E(y_{t-1})]\}\\
  &cov(y_t,y_{t-1})=E(y_t y_{t-1})-E(y_tE(y_{t-1}))-E(y_{t-1}E(y_t))+E(y_t)E(y_{t-1})\\
  &cov(y_t,y_{t-1})=E(y_t y_{t-1})-E(y_t)E(y_{t-1}))-E(y_t)E(y_{t-1})+E(y_t)E(y_{t-1})\\\\
  &\text{as } E(y_t)=E(y_{t-1})=\mu_y\\
  &cov(y_t,y_{t-1})=E(y_t y_{t-1})-\mu_y^2\\\\
  &\text{now}\\
  &E(y_t y_{t-1})=E([c+\varphi y_{t-1} +\epsilon_t] y_{t-1})\\
  &E(y_t y_{t-1})=cE(y_{t-1})+\varphi E(y_{t-1}^2)+E(\epsilon_ty_{t-1})\\
  &E(y_t y_{t-1})=c\mu_y+\varphi(\sigma_y^2-\mu_y^2)\\\\
  &\text{so}\\
  &cov(y_t,y_{t-1})=c\mu_y+\varphi(\sigma_y^2-\mu_y^2)-\mu_y^2\\
  &cov(y_t,y_{t-1})=c^2+\varphi(\sigma_y^2-c^2)-c^2\\
  &cov(y_t,y_{t-1})=\varphi(\sigma_y^2-c^2)\\\\
  &\text{now}\\
  &cov(y_t,y_{t-2})=E(y_t y_{t-2})-\mu_y^2\\\\
  &\text{here}\\
  &E(y_t y_{t-2})=E([c+\varphi y_{t-1} +\epsilon_t] y_{t-2})\\
  &E(y_t y_{t-2})=E([c+\varphi(c+\varphi y_{t-2} +\epsilon_{t-1}) +\epsilon_t] y_{t-2})\\
   &E(y_t y_{t-2})=cE(y_{t-2})+\varphi cE(y_{t-2})+\varphi^2E(y_{t-2}^2)+\varphi E(\epsilon_{t-1}y_{t-2})+E(\epsilon_ty_{t-2})\\
   &E(y_t y_{t-2})=c\mu_y+\varphi c\mu_y+\varphi^2(\sigma_y^2-\mu_y^2)\\
  &cov(y_t,y_{t-2})=c\mu_y+\varphi c\mu_y+\varphi^2(\sigma_y^2-\mu_y^2)-\mu_y^2\\
  &cov(y_t,y_{t-2})=c^2+\varphi c^2+\varphi^2(\sigma_y^2-c^2)-c^2\\
  &cov(y_t,y_{t-2})=\varphi c^2+\varphi^2(\sigma_y^2-c^2)\\\\
  &\text{so in general we have }\\
  &cov(y,y_{y-k})=\varphi^{k}(\sigma_y^2-c^2) +c^2\sum_{i=0}^{k-1} \varphi^i
  \end{align} %]]></script></p>
  </li>
  <li>
    <p>Autocorrelation 
<script type="math/tex">% <![CDATA[
\begin{align}
&cor(y_t,y_{t-k})=\frac{cov(y_t,y_{t-k})}{\sigma_{y_t}\sigma_{y_{t-k}}}\\
&cor(y_t,y_{t-k})=\frac{\varphi^{k}(\sigma_y^2-c^2) +c^2\sum_{i=0}^{k-1} \varphi^i}{\sigma_y^2}\\\\
&\text{if } c=0 \text{ then}\\
&cor(y_t,y_{t-k})=\varphi^k\\
\end{align} %]]></script>
  so for \(AR(1)\) model Autocorrelation function will deacy exponentially as k increases as \(|\varphi|&lt;1\).</p>

    <p>Finally, the partial autocorrelation function (PACF) involves plotting the estimated coefficient \(Y_{t−k}\)from an OLS estimate of an \(AR(k) \)process, against k. If the observations are generated by an \(AR(p)\) process then the theoretical partial autocorrelations will be high and significant for up to p lags and zero for lags beyond p.</p>
  </li>
</ul>

<h2 id="i-model">I Model</h2>
<p><strong>Intregated process</strong> used to replace  data values by diffrencing values.
so</p>

<p>\(\Delta y_t=y_t-y_{t-1}\)</p>

<p>in general</p>

<p>\(\Delta^dy_t=\Delta^{d-1}y_t-\Delta^{d-1}y_{t-1}\)</p>

<p>In \(I(d)\) model d represent the number of diffrencing.</p>

<h2 id="ma-model">MA Model</h2>
<p><strong>Moving Average model</strong> 
 is conceptually a linear regression of the current output value of the series against current and previous (observed) white noise error terms or random shocks.
Let \(y_t\) be a time series then \(MA(q)\) MA of order q is defined as 
<script type="math/tex">y_t=\mu + \epsilon_t+\theta_1\epsilon_{t-1}+...+\theta_q\epsilon_{t-q}</script></p>

<p>where \(\mu\) is mean of time series and \(\epsilon_t\) white noise terms.</p>

<p>this can be rewritten as</p>

<script type="math/tex; mode=display">y_t=\mu +\epsilon_t+\sum_{i=1}^q \theta_i \epsilon_{t-i}</script>

<p>using lag operator we have</p>

<script type="math/tex; mode=display">y_t=\mu+(1+\theta_1L+\theta_2L^2+.......+\theta_qL^q)\epsilon_t</script>

<p>or</p>

<script type="math/tex; mode=display">y_t=\theta(L)\epsilon_t</script>

<p>Because any \(MA(q)\) model is by definition average of q stationary white noise process so every \(MA(q)\) model is stationary as long as q is finite.</p>

<ul>
  <li>
    <p>Invertibility of MA Model
  consider a \(MA(1)\) model</p>

    <script type="math/tex; mode=display">y_t=\epsilon_t+\theta\epsilon_{t-1}</script>

    <p>using lag operator we can write</p>

    <p><script type="math/tex">% <![CDATA[
\begin{align}
  &y_t=(1+\theta L)\epsilon_t\\
  &\epsilon_t=y_t(1+\theta L)^{-1}\\\\
  &\text{if } | \theta | <1 \text{ above equation can be considered as sum of an infinite gp series}\\\\
  &\epsilon_t=y_t(1-\theta L +\theta^2 L^2-\theta^3 L^3+......)
  \end{align} %]]></script>
  so any \(MA(q)\) model can be converted into infnite \(AR\) process with geometrically declining weights if \(|\theta|&lt;1\).</p>
  </li>
</ul>

<p>Properties of \(MA(1)\) model
Ignorig the term \mu for easier calculation.</p>

<ul>
  <li>
    <p>Mean
  It is clearly zero as it is mean of white noise.</p>

    <script type="math/tex; mode=display">\mu_y=0</script>
  </li>
  <li>
    <p>Variance 
<script type="math/tex">% <![CDATA[
\begin{align}
&var(y_t)=E(y_t^2)-E(\mu_{y_t})\\
&\sigma_{y}^2=E([\epsilon_t+\theta\epsilon_{t-1}]^2)\\
&\sigma_{y}^2=E([\epsilon_t^2)+\theta^2 E([\epsilon_t^2)+2\theta E(\epsilon_t)\\
&\sigma_{y}^2=\sigma_{\epsilon}^2+\theta^2 \sigma_\epsilon^2\\
\end{align} %]]></script></p>
  </li>
  <li>
    <p>Covariance
<script type="math/tex">% <![CDATA[
\begin{align}
&cov(y_t,y_{t-1})=E([\epsilon_t+\theta\epsilon_{t_1}][\epsilon_{t-1}+\theta\epsilon_{t-2}])\\
&cov(y_t,y_{t-1})=E(\epsilon_t\epsilon_{t-1})+\theta E(\epsilon_t\epsilon_{t-2})+\theta E(\epsilon_{t-1}^2)+\theta^2 E(\epsilon_{t-1}\epsilon_{t-2})\\\\
&\text{as } \epsilon_t \text{ is serially uncorelated as it is random data}\\
&cov(y_t,y_{t-1})=\theta \sigma_\epsilon^2\\\\
&\text{now}\\
&cov(y_t,y_{t-2})=E([\epsilon_t+\theta\epsilon_{t_1}][\epsilon_{t-2}+\theta\epsilon_{t-3}])\\
&cov(y_t,y_{t-2})=E(\epsilon_t\epsilon_{t-2})+\theta E(\epsilon_t\epsilon_{t-3})+\theta E(\epsilon_{t-1}\epsilon_{t-2})+\theta^2 E(\epsilon_{t-1}\epsilon_{t-3})\\\\
&\text{as } \epsilon_t \text{ is serially uncorelated as it is random data}\\
&cov(y_t,y_{t-2})=0\\
&cov(y_t,y_{t-k})=\begin{cases} \theta \sigma_\epsilon^2 & k=0\\ 0 && k>1\end{cases}
\end{align} %]]></script></p>
  </li>
  <li>
    <p>Autocorrelation</p>
  </li>
</ul>

<p><script type="math/tex">% <![CDATA[
\begin{align}
&\text{we have}\\
&cor(y_t,y_{t-k})=\frac{cor(y_t,y_{t-k})}{\sigma_{y_t}\sigma_{y_{t-k}}}\\
&cor(y_t,y_{t-k})=\begin{cases}\frac{\theta}{1+\theta^2}& k=1\\ 0 & k>1\end{cases}\\
\end{align} %]]></script>
    So, with an \(MA(q)\) model the correlogram (the graph of the ACF) is expected to have q spikes for \(k = q\), and then go down to zero immediately. Also, since any MA process can be represented as an AR process with geometrically declining coefficients, the PACF for an MA process should decay slowly.</p>

<h2 id="arma">ARMA</h2>
<p>\(ARMA(p,q)\) is combination of \(AR(p)\) and \(MA(q)\) models.</p>

<p>The general form af \(ARMA(p,q)\) model excluding constants can be represented as
   <script type="math/tex">% <![CDATA[
\begin{align}
   &y_t=\sum_{i=0}^p\varphi_i y_{t-i} + \epsilon_t+\sum_{j=0}^q\theta_j\epsilon_{j-q}\\\\
   &\text{using lag operator we have}\\
   &y_t(1-\varphi_1L-\varphi_2L^2-...+\varphi_pL^p)=(1+\theta_1L+\theta_2L^2+.....+\theta_qL^q)\epsilon_t\\
   &\varphi(L)y_t=\theta(L)u_t\\
   \end{align} %]]></script></p>

<p>here \(p\) roots of pollynomail \(\varphi(z)=0\) should lie 
   outside unit circle for stationary and \(q\) roots of pollynomail \(\theta(z)=0\) should lie 
   outside unit circle for invertibility.</p>

<h2 id="arima">ARIMA</h2>
<p>\(ARMA(p,d,q)\) is combination of \(AR(p)\),\(I(d)\) and \(MA(q)\) models.
To give an example of an \(ARIMA(p, d, q)\) model, we can say that in general an inte-
grated series of order \(d\) must be differenced \(d\) times before it can be represented by a
stationary and invertible ARMA process.
if a process \(y_t\) has an ARIMA(p, d, q) representation, then the  \(\Delta^d y_t\) has
an \(ARMA(p, q)\) representation, as presented by this equation:</p>

<script type="math/tex; mode=display">\Delta^dy_t(1-\varphi_1 L-\varphi_2 L^2-....-\varphi_p L^p)=(1+\theta_1L+\theta_2L^2+.....+\theta_qL^q)\epsilon_t</script>

<h2 id="boxjenkins-model-selection">Box–Jenkins model selection</h2>
<p><strong>Akaike information criterion (AIC)</strong> is an estimator of out-of-sample prediction error and thereby relative quality of statistical models for a given set of data.</p>

<p><strong>Schwarz Bayesian criterion (SBC)</strong></p>

<p>The Box–Jenkins approach involves the following steps:</p>

<p><strong>Step 1:</strong> Calculate the ACF and PACF of the raw data, and check whether the series is
stationary or not. If the series is stationary, go to step 3; if not, go to step 2.</p>

<p><strong>Step 2:</strong> Take the logarithm and the first differences of the raw data and calculate the
ACF and PACF for the first logarithmic differenced series.</p>

<p><strong>Step 3:</strong> Examine the graphs of the ACF and PACF and determine which models would
be good starting points choose according the table.</p>

<p><strong>Step 4:</strong> Estimate those models.</p>

<p><strong>Step 5:</strong> For each of the estimated models:</p>

<ul>
  <li>check to see if the parameter of the longest lag is significant. If not, there are probably too many parameters and you should decrease the order of p and/or q.</li>
  <li>check the ACF and PACF of the errors. If the model has at least enough parameters, then all error ACFs and PACFs will be insignificant.</li>
  <li>check the Akaike information criterion (AIC) and the Schwarz Bayesian criterion (SBC).together with the adj-R 2 of the estimated models to detect which model is the parsimonious one (that is the one that minimizes AIC and SBC and has the highest adj-R 2 ).Of the two criteria, the SBC is preferable.</li>
</ul>

<p><strong>Step 6:</strong>  If changes in the original model are needed, go back to step 4.</p>

<table>
  <thead>
    <tr>
      <th>Model</th>
      <th>ACF</th>
      <th>PACF</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>White noise</td>
      <td>All Autocorrelation are zero</td>
      <td>All partial correlations are zero</td>
    </tr>
    <tr>
      <td>\(MA(1)\)</td>
      <td>Single positive spike at lag 1</td>
      <td>Damped sine wave or exponential decay</td>
    </tr>
    <tr>
      <td>\(AR(1)\)</td>
      <td>Damped sine wave or exponential decay</td>
      <td>Single positive spike at lag 1</td>
    </tr>
    <tr>
      <td>\(MA(q)\)</td>
      <td>spikes upto lag q then die imemediately</td>
      <td>Damped sine wave or exponential decay</td>
    </tr>
    <tr>
      <td>\(AR(q)\)</td>
      <td>Damped sine wave or exponential decay</td>
      <td>spikes upto lag p then die imemediately</td>
    </tr>
    <tr>
      <td>\( ARMA(p,q) \)</td>
      <td>Decay [Exp. or sine wave] start at lag q</td>
      <td>Decay [Exp. or sine wave] start at lag p</td>
    </tr>
  </tbody>
</table>

<p>Lets go and use arima model on data using python</p>

<h2 id="projectusing-python-for-time-series-analysis">Project:using python for Time series analysis</h2>
<p>using above analysis on a seasonal time series data</p>

<h3 id="read-data">Read Data</h3>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s">'monthly-milk-production-pounds-p.csv'</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="o">.</span><span class="n">tail</span><span class="p">()</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Monthly milk production: pounds per cow. Jan 62 ? Dec 75</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>164</td>
      <td>1975-09</td>
      <td>817.0</td>
    </tr>
    <tr>
      <td>165</td>
      <td>1975-10</td>
      <td>827.0</td>
    </tr>
    <tr>
      <td>166</td>
      <td>1975-11</td>
      <td>797.0</td>
    </tr>
    <tr>
      <td>167</td>
      <td>1975-12</td>
      <td>843.0</td>
    </tr>
    <tr>
      <td>168</td>
      <td>Monthly milk production: pounds per cow. Jan 6...</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="c1"># Weird last value at bottom causing issues
</span><span class="n">df1</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="mi">168</span><span class="p">,</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span><span class="n">inplace</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">index</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Index</span><span class="p">(</span><span class="n">sm</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">datetools</span><span class="o">.</span><span class="n">dates_from_range</span><span class="p">(</span><span class="s">'1962M1'</span><span class="p">,</span> <span class="s">'1975M12'</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">index</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>Timestamp('1975-12-31 00:00:00')
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="o">.</span><span class="n">index</span><span class="o">=</span><span class="n">index</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Monthly milk production: pounds per cow. Jan 62 ? Dec 75</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1962-01-31</td>
      <td>1962-01</td>
      <td>589.0</td>
    </tr>
    <tr>
      <td>1962-02-28</td>
      <td>1962-02</td>
      <td>561.0</td>
    </tr>
    <tr>
      <td>1962-03-31</td>
      <td>1962-03</td>
      <td>640.0</td>
    </tr>
    <tr>
      <td>1962-04-30</td>
      <td>1962-04</td>
      <td>656.0</td>
    </tr>
    <tr>
      <td>1962-05-31</td>
      <td>1962-05</td>
      <td>727.0</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s">'Month'</span><span class="p">],</span><span class="mi">1</span><span class="p">,</span><span class="n">inplace</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">df1</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">]</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span><span class="o">.</span><span class="n">T</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Milk in pounds per cow</td>
      <td>168.0</td>
      <td>754.708333</td>
      <td>102.204524</td>
      <td>553.0</td>
      <td>677.75</td>
      <td>761.0</td>
      <td>824.5</td>
      <td>969.0</td>
    </tr>
  </tbody>
</table>
</div>

<h3 id="visualize-data">Visualize data</h3>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">));</span>
</code></pre></div></div>

<p><img src="output_75_0.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">timeseries1</span> <span class="o">=</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">]</span>
<span class="n">timeseries1</span><span class="o">.</span><span class="n">rolling</span><span class="p">(</span><span class="mi">12</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">label</span><span class="o">=</span><span class="s">'12 Month Rolling Mean'</span><span class="p">)</span>
<span class="n">timeseries1</span><span class="o">.</span><span class="n">rolling</span><span class="p">(</span><span class="mi">12</span><span class="p">)</span><span class="o">.</span><span class="n">std</span><span class="p">()</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">label</span><span class="o">=</span><span class="s">'12 Month Rolling Std'</span><span class="p">)</span>
<span class="n">timeseries1</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.legend.Legend at 0x7f8d373f54d0&gt;
</code></pre></div></div>

<p><img src="output_76_1.png" alt="\time-series-data\png" /></p>

<h3 id="decomposition">Decomposition</h3>
<p>To see individaul parts</p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="kn">from</span> <span class="nn">statsmodels.tsa.seasonal</span> <span class="kn">import</span> <span class="n">seasonal_decompose</span>
<span class="n">decomposition</span> <span class="o">=</span> <span class="n">seasonal_decompose</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">],</span> <span class="n">freq</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span>  
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>  
<span class="n">fig</span> <span class="o">=</span> <span class="n">decomposition</span><span class="o">.</span><span class="n">plot</span><span class="p">()</span>  
<span class="n">fig</span><span class="o">.</span><span class="n">set_size_inches</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">8</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;Figure size 432x288 with 0 Axes&gt;
</code></pre></div></div>

<p><img src="output_78_1.png" alt="\time-series-data\png" /></p>

<h3 id="testing-for-stationary">Testing for Stationary</h3>

<p>We are going to use an augmented Dickey–Fuller  (ADF) hypothesis test</p>

<p><strong>H0</strong> Null hypothesis : Time series has a unit root,indicating it is non-stationary.</p>

<p><strong>H1</strong> Alternative hypothesis: Time series has no  unit root,indicating it is stationary.</p>

<ul>
  <li>
    <p>A small p-value (typically ≤ 0.05) indicates strong evidence against the null hypothesis, so you reject the null hypothesis.</p>
  </li>
  <li>
    <p>A large p-value (&gt; 0.05) indicates weak evidence against the null hypothesis, so you fail to reject the null hypothesis.</p>
  </li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="kn">from</span> <span class="nn">statsmodels.tsa.stattools</span> <span class="kn">import</span> <span class="n">adfuller</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">result</span> <span class="o">=</span> <span class="n">adfuller</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">])</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">result</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>(-1.3038115874221246,
 0.627426708603034,
 13,
 154,
 {'1%': -3.473542528196209,
  '5%': -2.880497674144038,
  '10%': -2.576878053634677},
 1115.1730447395112)
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="c1"># Store in a function for later use!
</span><span class="k">def</span> <span class="nf">adf_check</span><span class="p">(</span><span class="n">time_series</span><span class="p">):</span>
    <span class="s">"""
    Function to return formated adfuller test results 
    Parameters time series 
    """</span>
    <span class="n">result</span> <span class="o">=</span> <span class="n">adfuller</span><span class="p">(</span><span class="n">time_series</span><span class="p">)</span>
    <span class="k">print</span><span class="p">(</span><span class="s">'Augmented Dickey-Fuller Test:'</span><span class="p">)</span>
    <span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s">'ADF Test Statistic'</span><span class="p">,</span><span class="s">'p-value'</span><span class="p">,</span><span class="s">'#Lags Used'</span><span class="p">,</span><span class="s">'Number of Observations Used'</span><span class="p">]</span>

    <span class="k">for</span> <span class="n">value</span><span class="p">,</span><span class="n">label</span> <span class="ow">in</span> <span class="nb">zip</span><span class="p">(</span><span class="n">result</span><span class="p">,</span><span class="n">labels</span><span class="p">):</span>
        <span class="k">print</span><span class="p">(</span><span class="n">label</span><span class="o">+</span><span class="s">' : '</span><span class="o">+</span><span class="nb">str</span><span class="p">(</span><span class="n">value</span><span class="p">)</span> <span class="p">)</span>
    
    <span class="k">if</span> <span class="n">result</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span> <span class="o">&lt;=</span> <span class="mf">0.05</span><span class="p">:</span>
        <span class="k">print</span><span class="p">(</span><span class="s">"strong evidence against the null hypothesis, reject the null hypothesis. Data has no unit root and is stationary"</span><span class="p">)</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="k">print</span><span class="p">(</span><span class="s">"weak evidence against null hypothesis, time series has a unit root, indicating it is non-stationary "</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">adf_check</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">])</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>Augmented Dickey-Fuller Test:
ADF Test Statistic : -1.3038115874221246
p-value : 0.627426708603034
#Lags Used : 13
Number of Observations Used : 154
weak evidence against null hypothesis, time series has a unit root, indicating it is non-stationary 
</code></pre></div></div>

<h3 id="differencing">Differencing</h3>
<p>To make df1  timeseries stationary</p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">]</span> <span class="o">=</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">]</span> <span class="o">-</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">]</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'Milk Second Difference'</span><span class="p">]</span> <span class="o">=</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">]</span> <span class="o">-</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal Difference'</span><span class="p">]</span> <span class="o">=</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">]</span> <span class="o">-</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">]</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">12</span><span class="p">)</span>

</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="c1">#remove null values caused by shift method
</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">df1</span><span class="p">[</span><span class="s">'Milk Second Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d3770c310&gt;
</code></pre></div></div>

<p><img src="output_90_1.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'Milk Second Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d376be950&gt;
</code></pre></div></div>

<p><img src="output_91_1.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d37b03ed0&gt;
</code></pre></div></div>

<p><img src="output_92_1.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">adf_check</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">])</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>Augmented Dickey-Fuller Test:
ADF Test Statistic : -3.0549955586530553
p-value : 0.03006800400178688
#Lags Used : 14
Number of Observations Used : 152
strong evidence against the null hypothesis, reject the null hypothesis. Data has no unit root and is stationary
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">adf_check</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk Second Difference'</span><span class="p">])</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>Augmented Dickey-Fuller Test:
ADF Test Statistic : -14.327873645603336
p-value : 1.1126989332083069e-26
#Lags Used : 11
Number of Observations Used : 154
strong evidence against the null hypothesis, reject the null hypothesis. Data has no unit root and is stationary
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">adf_check</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal Difference'</span><span class="p">])</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>Augmented Dickey-Fuller Test:
ADF Test Statistic : -2.3354193143593993
p-value : 0.16079880527711304
#Lags Used : 12
Number of Observations Used : 143
weak evidence against null hypothesis, time series has a unit root, indicating it is non-stationary 
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal First Difference'</span><span class="p">]</span> <span class="o">=</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">]</span> <span class="o">-</span> <span class="n">df1</span><span class="p">[</span><span class="s">'Milk First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">12</span><span class="p">)</span>
<span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d37a0f490&gt;
</code></pre></div></div>

<p><img src="output_96_1.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">"Seasonal First Difference"</span><span class="p">]</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">adf_check</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">dropna</span><span class="p">())</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>Augmented Dickey-Fuller Test:
ADF Test Statistic : -5.038002274921985
p-value : 1.86542343187882e-05
#Lags Used : 11
Number of Observations Used : 143
strong evidence against the null hypothesis, reject the null hypothesis. Data has no unit root and is stationary
</code></pre></div></div>

<p><strong>Note:</strong> For Arima model we are going to use seasnal first diffrence as clearly our data has a seasonality and seasnal first diffrence is stationary</p>

<h3 id="acf-and-pacf">ACF and PACF</h3>
<p>To choose appropaite model and its parameters</p>

<ul>
  <li>Identification of an AR model is often best done with the PACF.
    <ul>
      <li>For an AR model, the theoretical PACF “shuts off” past the order of the model.  The phrase “shuts off” means that in theory the partial autocorrelations are equal to 0 beyond that point.  Put another way, the number of non-zero partial autocorrelations gives the order of the AR model.  By the “order of the model” we mean the most extreme lag of x that is used as a predictor.</li>
    </ul>
  </li>
  <li>Identification of an MA model is often best done with the ACF rather than the PACF.
    <ul>
      <li>For an MA model, the theoretical PACF does not shut off, but instead tapers toward 0 in some manner.  A clearer pattern for an MA model is in the ACF.  The ACF will have non-zero autocorrelations only at lags involved in the model.</li>
    </ul>
  </li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="kn">from</span> <span class="nn">statsmodels.graphics.tsaplots</span> <span class="kn">import</span> <span class="n">plot_acf</span><span class="p">,</span><span class="n">plot_pacf</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">fig_first</span> <span class="o">=</span> <span class="n">plot_acf</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">"Milk First Difference"</span><span class="p">]</span><span class="o">.</span><span class="n">dropna</span><span class="p">(),</span><span class="n">lags</span><span class="o">=</span><span class="mi">125</span><span class="p">)</span>
</code></pre></div></div>

<p><img src="output_102_0.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">fig_seasonal_first</span> <span class="o">=</span> <span class="n">plot_acf</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">"Seasonal First Difference"</span><span class="p">]</span><span class="o">.</span><span class="n">dropna</span><span class="p">(),</span><span class="n">lags</span><span class="o">=</span><span class="mi">125</span><span class="p">)</span>
</code></pre></div></div>

<p><img src="output_103_0.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">8</span><span class="p">))</span>
<span class="n">ax1</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="mi">211</span><span class="p">)</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">sm</span><span class="o">.</span><span class="n">graphics</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">plot_acf</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">13</span><span class="p">:],</span> <span class="n">lags</span><span class="o">=</span><span class="mi">40</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax1</span><span class="p">)</span>
<span class="n">ax2</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="mi">212</span><span class="p">)</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">sm</span><span class="o">.</span><span class="n">graphics</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">plot_pacf</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Seasonal First Difference'</span><span class="p">]</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">13</span><span class="p">:],</span> <span class="n">lags</span><span class="o">=</span><span class="mi">40</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax2</span><span class="p">)</span>
</code></pre></div></div>

<p><img src="output_104_0.png" alt="\time-series-data\png" /></p>

<p><strong>Note</strong></p>
<ul>
  <li>for df1  we are going to use AR(1) ,I(1) and  MA(1) with seasonality set to 12 as clearly indicated by above data analysis.</li>
  <li>just for comparison  we are going to use AR(1) ,I(1) and  MA(1).</li>
  <li>For comparison purpose we will also go for AR(2) and MA(2) models</li>
</ul>

<h3 id="using-model">Using Model</h3>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="c1"># FOR NON SEASONAL DATA 
</span><span class="kn">from</span> <span class="nn">statsmodels.tsa.arima_model</span> <span class="kn">import</span> <span class="n">ARIMA</span>
<span class="kn">import</span> <span class="nn">warnings</span>
<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s">'ignore'</span><span class="p">)</span>
</code></pre></div></div>

<p><code class="language-plaintext highlighter-rouge">help(ARIMA)</code> returns breif discription about the parameters of model</p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">model_ns</span><span class="o">=</span><span class="n">ARIMA</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">"Milk in pounds per cow"</span><span class="p">],(</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">))</span>
<span class="n">results_ns</span> <span class="o">=</span> <span class="n">model_ns</span><span class="o">.</span><span class="n">fit</span><span class="p">()</span>
<span class="k">print</span><span class="p">(</span><span class="n">results_ns</span><span class="o">.</span><span class="n">summary</span><span class="p">())</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>                                ARIMA Model Results                                 
====================================================================================
Dep. Variable:     D.Milk in pounds per cow   No. Observations:                  167
Model:                       ARIMA(1, 1, 1)   Log Likelihood                -873.331
Method:                             css-mle   S.D. of innovations             45.176
Date:                      Tue, 14 Jan 2020   AIC                           1754.662
Time:                              12:35:09   BIC                           1767.134
Sample:                          02-28-1962   HQIC                          1759.724
                               - 12-31-1975                                         
==================================================================================================
                                     coef    std err          z      P&gt;|z|      [0.025      0.975]
--------------------------------------------------------------------------------------------------
const                              1.5418      3.874      0.398      0.691      -6.052       9.135
ar.L1.D.Milk in pounds per cow     0.3873      0.249      1.555      0.122      -0.101       0.875
ma.L1.D.Milk in pounds per cow    -0.3203      0.246     -1.301      0.195      -0.803       0.162
                                    Roots                                    
=============================================================================
                  Real          Imaginary           Modulus         Frequency
-----------------------------------------------------------------------------
AR.1            2.5821           +0.0000j            2.5821            0.0000
MA.1            3.1218           +0.0000j            3.1218            0.0000
-----------------------------------------------------------------------------
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">model</span> <span class="o">=</span> <span class="n">sm</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">statespace</span><span class="o">.</span><span class="n">SARIMAX</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">],</span><span class="n">order</span><span class="o">=</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">0</span><span class="p">),</span> <span class="n">seasonal_order</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">))</span>
<span class="n">results</span> <span class="o">=</span> <span class="n">model</span><span class="o">.</span><span class="n">fit</span><span class="p">()</span>
<span class="k">print</span><span class="p">(</span><span class="n">results</span><span class="o">.</span><span class="n">summary</span><span class="p">())</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>                                 Statespace Model Results                                 
==========================================================================================
Dep. Variable:             Milk in pounds per cow   No. Observations:                  168
Model:             SARIMAX(0, 1, 0)x(1, 1, 2, 12)   Log Likelihood                -533.489
Date:                            Tue, 14 Jan 2020   AIC                           1074.977
Time:                                    12:35:12   BIC                           1087.151
Sample:                                01-31-1962   HQIC                          1079.922
                                     - 12-31-1975                                         
Covariance Type:                              opg                                         
==============================================================================
                 coef    std err          z      P&gt;|z|      [0.025      0.975]
------------------------------------------------------------------------------
ar.S.L12      -0.9997      0.210     -4.768      0.000      -1.411      -0.589
ma.S.L12       0.3940      1.717      0.230      0.818      -2.970       3.758
ma.S.L24      -0.5978      1.062     -0.563      0.574      -2.679       1.484
sigma2        53.5340     79.619      0.672      0.501    -102.517     209.585
===================================================================================
Ljung-Box (Q):                       35.87   Jarque-Bera (JB):                39.81
Prob(Q):                              0.66   Prob(JB):                         0.00
Heteroskedasticity (H):               0.68   Skew:                             0.81
Prob(H) (two-sided):                  0.17   Kurtosis:                         4.87
===================================================================================

Warnings:
[1] Covariance matrix calculated using the outer product of gradients (complex-step).
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">model</span> <span class="o">=</span> <span class="n">sm</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">statespace</span><span class="o">.</span><span class="n">SARIMAX</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">],</span><span class="n">order</span><span class="o">=</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">0</span><span class="p">),</span> <span class="n">seasonal_order</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">12</span><span class="p">))</span>
<span class="n">results</span> <span class="o">=</span> <span class="n">model</span><span class="o">.</span><span class="n">fit</span><span class="p">()</span>
<span class="k">print</span><span class="p">(</span><span class="n">results</span><span class="o">.</span><span class="n">summary</span><span class="p">())</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>                                 Statespace Model Results                                 
==========================================================================================
Dep. Variable:             Milk in pounds per cow   No. Observations:                  168
Model:             SARIMAX(0, 1, 0)x(2, 1, 1, 12)   Log Likelihood                -533.700
Date:                            Tue, 14 Jan 2020   AIC                           1075.400
Time:                                    12:35:12   BIC                           1087.574
Sample:                                01-31-1962   HQIC                          1080.345
                                     - 12-31-1975                                         
Covariance Type:                              opg                                         
==============================================================================
                 coef    std err          z      P&gt;|z|      [0.025      0.975]
------------------------------------------------------------------------------
ar.S.L12      -0.1305      0.206     -0.632      0.527      -0.535       0.274
ar.S.L24      -0.0965      0.124     -0.775      0.438      -0.340       0.147
ma.S.L12      -0.5028      0.202     -2.487      0.013      -0.899      -0.106
sigma2        55.1554      5.418     10.180      0.000      44.536      65.775
===================================================================================
Ljung-Box (Q):                       30.88   Jarque-Bera (JB):                33.12
Prob(Q):                              0.85   Prob(JB):                         0.00
Heteroskedasticity (H):               0.67   Skew:                             0.80
Prob(H) (two-sided):                  0.15   Kurtosis:                         4.61
===================================================================================

Warnings:
[1] Covariance matrix calculated using the outer product of gradients (complex-step).
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">model_s</span> <span class="o">=</span> <span class="n">sm</span><span class="o">.</span><span class="n">tsa</span><span class="o">.</span><span class="n">statespace</span><span class="o">.</span><span class="n">SARIMAX</span><span class="p">(</span><span class="n">df1</span><span class="p">[</span><span class="s">'Milk in pounds per cow'</span><span class="p">][:</span><span class="mi">150</span><span class="p">],</span><span class="n">order</span><span class="o">=</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">0</span><span class="p">),</span> <span class="n">seasonal_order</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">12</span><span class="p">))</span>
<span class="n">results_s</span> <span class="o">=</span> <span class="n">model_s</span><span class="o">.</span><span class="n">fit</span><span class="p">()</span>
<span class="k">print</span><span class="p">(</span><span class="n">results_s</span><span class="o">.</span><span class="n">summary</span><span class="p">())</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>                                 Statespace Model Results                                 
==========================================================================================
Dep. Variable:             Milk in pounds per cow   No. Observations:                  150
Model:             SARIMAX(0, 1, 0)x(1, 1, 1, 12)   Log Likelihood                -477.121
Date:                            Tue, 14 Jan 2020   AIC                            960.243
Time:                                    12:35:12   BIC                            969.003
Sample:                                01-31-1962   HQIC                           963.803
                                     - 06-30-1974                                         
Covariance Type:                              opg                                         
==============================================================================
                 coef    std err          z      P&gt;|z|      [0.025      0.975]
------------------------------------------------------------------------------
ar.S.L12      -0.0179      0.115     -0.155      0.877      -0.244       0.208
ma.S.L12      -0.6094      0.110     -5.532      0.000      -0.825      -0.394
sigma2        59.4337      6.206      9.576      0.000      47.269      71.598
===================================================================================
Ljung-Box (Q):                       36.37   Jarque-Bera (JB):                26.56
Prob(Q):                              0.63   Prob(JB):                         0.00
Heteroskedasticity (H):               1.11   Skew:                             0.79
Prob(H) (two-sided):                  0.73   Kurtosis:                         4.47
===================================================================================

Warnings:
[1] Covariance matrix calculated using the outer product of gradients (complex-step).
</code></pre></div></div>

<p><strong>Note:</strong> we are going to use results from seasonal ARIMA model   with paramets 1,1,1 and sesonality 12 as they  return least AIC and BIC values but for comparison we will also plot non seasonal ARIMA</p>

<h3 id="residue-plots">Residue Plots</h3>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">results_s</span><span class="o">.</span><span class="n">resid</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d377aa790&gt;
</code></pre></div></div>

<p><img src="output_115_1.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">results_s</span><span class="o">.</span><span class="n">resid</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s">'kde'</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d371e7810&gt;
</code></pre></div></div>

<p><img src="output_116_1.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">results_ns</span><span class="o">.</span><span class="n">resid</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">5</span><span class="p">))</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d370a13d0&gt;
</code></pre></div></div>

<p><img src="output_117_1.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">results_ns</span><span class="o">.</span><span class="n">resid</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s">'kde'</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7f8d370eea90&gt;
</code></pre></div></div>

<p><img src="output_118_1.png" alt="\time-series-data\png" /></p>

<p>Residue plots of non seasonal Arima shows a lot of error and clearly the kde is not normal distribution</p>

<h3 id="evalvation-of-predicted-values">Evalvation of Predicted values</h3>
<p>Predicting values that we know already</p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'forecast'</span><span class="p">]</span> <span class="o">=</span> <span class="n">results_s</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">start</span> <span class="o">=</span> <span class="mi">150</span><span class="p">,</span> <span class="n">end</span><span class="o">=</span> <span class="mi">168</span><span class="p">,</span> <span class="n">dynamic</span><span class="o">=</span> <span class="bp">True</span><span class="p">)</span>  
<span class="n">df1</span><span class="p">[[</span><span class="s">'Milk in pounds per cow'</span><span class="p">,</span><span class="s">'forecast'</span><span class="p">]]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">8</span><span class="p">));</span>
</code></pre></div></div>

<p><img src="output_121_0.png" alt="\time-series-data\png" /></p>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">df1</span><span class="p">[</span><span class="s">'forecast'</span><span class="p">]</span> <span class="o">=</span> <span class="n">results_s</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">start</span> <span class="o">=</span> <span class="mi">50</span><span class="p">,</span> <span class="n">end</span><span class="o">=</span> <span class="mi">168</span><span class="p">,</span> <span class="n">dynamic</span><span class="o">=</span> <span class="bp">True</span><span class="p">)</span>  
<span class="n">df1</span><span class="p">[[</span><span class="s">'Milk in pounds per cow'</span><span class="p">,</span><span class="s">'forecast'</span><span class="p">]]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">8</span><span class="p">));</span>
</code></pre></div></div>

<p><img src="output_122_0.png" alt="\time-series-data\png" /></p>

<p>as we decrease the start day the predictions show more devaition from actual data</p>

<h3 id="forecasting">Forecasting</h3>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="c1"># adding future datetime entries
</span><span class="kn">from</span> <span class="nn">pandas.tseries.offsets</span> <span class="kn">import</span> <span class="n">DateOffset</span>
<span class="n">future_dates</span> <span class="o">=</span> <span class="p">[</span><span class="n">df1</span><span class="o">.</span><span class="n">index</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">+</span> <span class="n">DateOffset</span><span class="p">(</span><span class="n">months</span><span class="o">=</span><span class="n">x</span><span class="p">)</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">24</span><span class="p">)</span> <span class="p">]</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">future_dates_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">index</span><span class="o">=</span><span class="n">future_dates</span><span class="p">[</span><span class="mi">1</span><span class="p">:],</span><span class="n">columns</span><span class="o">=</span><span class="n">df1</span><span class="o">.</span><span class="n">columns</span><span class="p">)</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">future_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">df1</span><span class="p">,</span><span class="n">future_dates_df</span><span class="p">])</span>
</code></pre></div></div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">future_df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Milk in pounds per cow</th>
      <th>Milk First Difference</th>
      <th>Milk Second Difference</th>
      <th>Seasonal Difference</th>
      <th>Seasonal First Difference</th>
      <th>forecast</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1962-01-31</td>
      <td>589.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1962-02-28</td>
      <td>561.0</td>
      <td>-28.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1962-03-31</td>
      <td>640.0</td>
      <td>79.0</td>
      <td>107.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1962-04-30</td>
      <td>656.0</td>
      <td>16.0</td>
      <td>-63.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1962-05-31</td>
      <td>727.0</td>
      <td>71.0</td>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">future_df</span><span class="o">.</span><span class="n">tail</span><span class="p">()</span>
</code></pre></div></div>

<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Milk in pounds per cow</th>
      <th>Milk First Difference</th>
      <th>Milk Second Difference</th>
      <th>Seasonal Difference</th>
      <th>Seasonal First Difference</th>
      <th>forecast</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1977-07-31</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1977-08-31</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1977-09-30</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1977-10-31</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1977-11-30</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">future_df</span><span class="p">[</span><span class="s">'forecast'</span><span class="p">]</span> <span class="o">=</span> <span class="n">results</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">start</span> <span class="o">=</span> <span class="mi">150</span><span class="p">,</span> <span class="n">end</span> <span class="o">=</span> <span class="mi">188</span><span class="p">,</span> <span class="n">dynamic</span><span class="o">=</span> <span class="bp">True</span><span class="p">)</span>  
<span class="n">future_df</span><span class="p">[[</span><span class="s">'Milk in pounds per cow'</span><span class="p">,</span> <span class="s">'forecast'</span><span class="p">]]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span> <span class="mi">8</span><span class="p">));</span>
</code></pre></div></div>

<p><img src="output_130_0.png" alt="\time-series-data\png" /></p>

<h1 id="conclusion">Conclusion</h1>

<h2 id="reference">Reference</h2>
<ul>
  <li>Applied Econometrics by  Dimitrios Asteriou, Stephen G. Hall.</li>
</ul>

<div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code>
</code></pre></div></div>


    <div class="tags">
        
        <b>Tags: </b>
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
    </div>




</div>

<hr class="shaded"/>

<footer>
            <div class="row">
                <div class="col-lg-12 footer">
               &copy;2020 Wajid Manzoor. All rights reserved. <br />
 
                </div>
            </div>
</footer>


        </div>
    <!-- /.row -->
</div>
<!-- /.container -->
</div>
<!-- /#main -->
    </div>

</body>

</html>
