
<!DOCTYPE html>
<!--[if lt IE 7 ]> <html lang="en" class="no-js ie6"> <![endif]-->
<!--[if IE 7 ]>    <html lang="en" class="no-js ie7"> <![endif]-->
<!--[if IE 8 ]>    <html lang="en" class="no-js ie8"> <![endif]-->
<!--[if IE 9 ]>    <html lang="en" class="no-js ie9"> <![endif]-->
<!--[if (gt IE 9)|!(IE)]><!--> <html lang="en" class="no-js"><!--<![endif]-->
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <title>Style Guide</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="shortcut icon" href="../favicon.ico" type="image/x-icon">
    <script src="../assets/javascripts/jquery-2.1.4.min.js"></script>
    
    <!-- Syntax Highligher -->
  	<script type="text/javascript" src="../assets/javascripts/syntaxhighlighter_3.0.83/scripts/shCore.js"></script>
  	<script type="text/javascript" src="../assets/javascripts/syntaxhighlighter_3.0.83/scripts/shBrushXml.js"></script>
  	<script type="text/javascript" src="../assets/javascripts/syntaxhighlighter_3.0.83/scripts/shBrushCss.js"></script>
  	<script type="text/javascript" src="../assets/javascripts/syntaxhighlighter_3.0.83/scripts/shBrushSass.js"></script>
  	<link type="text/css" rel="stylesheet" href="../assets/javascripts/syntaxhighlighter_3.0.83/styles/shCoreDefault.css"/>
  	
  	
  	<script type="text/javascript">
    	SyntaxHighlighter.all();
    	
    	function columnQuery(){
      	var windowW = $(window).width();
      	console.log(windowW);
      	$('[class*="span-"]').each(function(){
        	if(windowW > 768) {
          	$('[class*="span-xs-"]').removeClass(function (index, className) {
                return (className.match (/(^|\s)span-xs\S+/g) || []).join(' ');
            });
        	}
      	})
    	}
      
      $(document).ready(function(){
        columnQuery();
      })

    </script>

    <link rel="stylesheet" href="../assets/stylesheets/styles.css"  />
    <link rel="stylesheet" href="../assets/stylesheets/dev.css"  />

</head>
<body>
  
  <header>
    <div class="container">
      <h1>UIDUXEFEDIA Starter Sass &amp; Style Guide</h1>
      <span class="pull-right"><a class="btn ">Download</a></span>
    </div>
  </header>
  <div class="page-bdy">
      <nav>
        <h3>Features:</h3>
        <ul>
          <li><a href="#section-layout">Layout</a></li>
          <li><a href="#section-grids">Grids</a></li>
          <li><a href="#section-mixins">Sass Mixins</a></li>
          <li><a href="#section-tags">HTML tags</a></li>
        </ul>
      </nav>
      <div id="main">

        <div class="anchor" id="section-layout"></div>
        <section>
          <h1 class="section-head">Layouts</h1>
          <fieldset>
            <p>There are a couple built-in layouts, including a fixed header and left area with a scrollable right area as well as a fixed header, footer and left area with a scrollable right area. </p>
            
            <div class="code">
              <h2>Fixed Header, Fixed Left, Scrollable Right</h2>
              <pre class="brush:xml">
                  <!-- Within <body> -->
                  <header>...</header>
                  <div class="page-bdy">
                    <nav>...</nav>
                    <div id="main">
                      ...
                    </div>
                  </div>
              </pre>

              <h2>Fixed Header, Fixed Footer, Fixed Left, Scrollable Right</h2>
              <pre class="brush:xml">
                  <!-- Within <body> -->
                  <header>...</header>
                  <div class="page-bdy wfooter">
                    <nav>...</nav>
                    <div id="main">
                      ...
                    </div>
                  </div>
                  <footer>...</footer>
              </pre>

              <p>Layout dimensions can be easily altered from within _variables.scss. </p>
              <pre class="brush:sass">
                /* Within _variables.scss */
                
                $headerh:     78px;
                $footerh:     38px;
                $navw:        120px;
                
                $sectionw:    1370px; // Max-width on sections in #main
                $contentw:    $navw + $sectionw + 70px; // Width of nav, #main and #main X-axis padding 
                
                $navpadding:  25px 0 0 40px; // Padding on nav element
                $mainpadding: 0 40px 0 30px; // Padding on #main element (Sum of X-axis padding properties to be added to $contentw variable) 
                $containerp:  0 40px 0 30px; // Padding on .container element (Usually same left padding as nav and right padding as #main)
                
              </pre>
            </div>
            
          </fieldset>
        </section>
                
        <div class="anchor" id="section-grids"></div>
        <section>
          <h1 class="section-head">Grids</h1>
          <fieldset>
            
            <p>Grids can be used using a similar syntax to Bootstrap's grid system, but can be customized to have any number of columns desired and fixed width gutters. Grid sets are created using an each and for loop in _layout.scss, but can easily be added and removed with a few quick changes from within _variables.scss.</p>

            <div class="code">
              <h2>Sass</h2>
              <pre class="brush:sass">
                /* Within _variables.scss */
                
                $gridlist: ('five' 5 10px 12px) ('ten' 10 20px 50px); 
                
                /* 
                Each set of parenthesis is a new grid set 
                First value is the grid name
                Second value is number of columns 
                Third value is gutter width 
                Fourth value is row margin 
                */
              </pre>
              <p>In this example, three grid sets are created:</p>
              <ul>
                <li>5 Column Grid with 10px gutter between columns and 12px between rows</li>
                <li>10 Column Grid with 20px gutter between columns and 50px between rows</li>
              </ul>
            </div>
            
            <div class="code">
              <h2>A 5-Column Grid</h2>
              <pre class="brush:xml">
                <div class="grid-five">
                  <div class="row">
                    <div class="col-sm-1 col-md-2 faded">SPAN 2</div>
                    <div class="col-sm-1 col-md-3 faded">SPAN 3</div>
                    <div class="col-sm-1 col-md-5 faded">SPAN 5</div>
                    <div class="col-sm-1 col-md-4 faded">SPAN 4</div>
                    <div class="col-sm-1 col-md-1 faded">SPAN 1</div>
                  </div>
                </div>
              </pre>

              <p><strong>Example:</strong></p>
              <div class="grid-five">
                <div class="row">
                    <div class="col-sm-1 col-md-2 faded">SPAN 2</div>
                    <div class="col-sm-1 col-md-3 faded">SPAN 3</div>
                    <div class="col-sm-1 col-md-5 faded">SPAN 5</div>
                    <div class="col-sm-1 col-md-4 faded">SPAN 4</div>
                    <div class="col-sm-1 col-md-1 faded">SPAN 1</div>
                </div>
              </div>
            </div>

            <div class="code">
              <h2>A 10-Column Grid</h2>
              <pre class="brush:xml">
              <div class="grid-ten">
                <div class="row">
                    <div class="col-sm-1 col-md-2 faded">SPAN 2</div>
                    <div class="col-sm-1 col-md-3 faded">SPAN 3</div>
                    <div class="col-sm-1 col-md-5 faded">SPAN 5</div>
                    <div class="col-sm-1 col-md-6 faded">SPAN 6</div>
                    <div class="col-sm-1 col-md-4 faded">SPAN 4</div>
                </div>
              </div>
              </pre>
              
              <p><strong>Example:</strong></p>
              <div class="grid-ten">
                <div class="row">
                    <div class="col-sm-1 col-md-2 faded">SPAN 2</div>
                    <div class="col-sm-1 col-md-3 faded">SPAN 3</div>
                    <div class="col-sm-1 col-md-5 faded">SPAN 5</div>
                    <div class="col-sm-1 col-md-6 faded">SPAN 6</div>
                    <div class="col-sm-1 col-md-4 faded">SPAN 4</div>
                </div>
              </div>

          </fieldset>
        </section>

        <div class="anchor" id="section-mixins"></div>
        <section>
          <h1 class="section-head">Mixins</h1>
          <fieldset>
            <p>There are a couple built-in mixins described below. </p>
            
            <div class="code">
              <h2>Fixed Header, Fixed Left, Scrollable Right</h2>
              <pre class="brush:xml">
                  <!-- Within <body> -->
                  <header>...</header>
                  <div class="page-bdy">
                    <nav>...</nav>
                    <div id="main">
                      ...
                    </div>
                  </div>
              </pre>

              <h2>Fixed Header, Fixed Footer, Fixed Left, Scrollable Right</h2>
              <pre class="brush:xml">
                  <!-- Within <body> -->
                  <header>...</header>
                  <div class="page-bdy wfooter">
                    <nav>...</nav>
                    <div id="main">
                      ...
                    </div>
                  </div>
                  <footer>...</footer>
              </pre>

              <p>Layout dimensions can be easily altered from within _variables.scss. </p>
              <pre class="brush:sass">
                /* Within _variables.scss */
                
                $headerh:     78px;
                $footerh:     38px;
                $navw:        120px;
                
                $sectionw:    1370px; // Max-width on sections in #main
                $contentw:    $navw + $sectionw + 70px; // Width of nav, #main and #main X-axis padding 
                
                $navpadding:  25px 0 0 40px; // Padding on nav element
                $mainpadding: 0 40px 0 30px; // Padding on #main element (Sum of X-axis padding properties to be added to $contentw variable) 
                $containerp:  0 40px 0 30px; // Padding on .container element (Usually same left padding as nav and right padding as #main)
                
              </pre>
            </div>
            
          </fieldset>
        </section>
        
      
        <div class="anchor" id="section-tags"></div>
        <section>
          <h1 class="section-head">HTML Tags</h1>
          <fieldset>

            <p>Within assets/stylesheets/scss/_partials, there is a blank tags.scss file to develop most commonly used standard HTML tags. 
            
          </fieldset>        
      </div>
  </div>

</body>
</html>
