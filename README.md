# standford-core-nlp
A Part-Of-Speech Tagger (POS Tagger) is a piece of software that reads text in some language and assigns parts of speech to each word (and other token), such as noun, verb, adjective, etc., although generally computational applications use more fine-grained POS tags like 'noun-plural'. This software is a Java implementation of the log-linear part-of-speech taggers described in these papers (if citing just one paper, cite the 2003 one):

<!DOCTYPE html>
<html lang="en">
<html>
  <head>

 <meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="">
<meta name="keywords" content=" pos">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@stanfordnlp">
<meta name="twitter:creator" content="@stanfordnlp">
<meta name="twitter:title" content="Stanford CoreNLP">
<meta name="twitter:description" content="High-performance human language analysis tools. Widely used, available open source; written in Java.">
<meta name="twitter:image" content="https://stanfordnlp.github.io/CoreNLP/images/Cate-Blanchett.png">
<title>POSTaggerAnnotator  | Stanford CoreNLP</title>
<link rel="stylesheet" type="text/css" href="https://stanfordnlp.github.io/CoreNLP/css/syntax.css">
<link rel="stylesheet" type="text/css" href="https://stanfordnlp.github.io/CoreNLP/css/font-awesome.min.css">
<link rel="stylesheet" type="text/css" href="https://stanfordnlp.github.io/CoreNLP/css/bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://stanfordnlp.github.io/CoreNLP/css/modern-business.css">
<link rel="stylesheet" type="text/css" href="https://stanfordnlp.github.io/CoreNLP/css/lavish-bootstrap.css">
<link rel="canonical" href="/pos.html">
<link rel="stylesheet" type="text/css" href="https://stanfordnlp.github.io/CoreNLP/css/customstyles.css">
<link rel="stylesheet" type="text/css" href="https://stanfordnlp.github.io/CoreNLP/css/theme-cardinal.css">
<link rel="canonical" href="/pos.html">
<link rel="alternate" type="application/rss+xml" title="CoreNLP" href="feed.xml" />
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-cookie/1.4.1/jquery.cookie.min.js"></script>
<script src="js/jquery.navgoco.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/js/bootstrap.min.js"></script>
<script src="js/toc.js"></script>
<script src="js/customscripts.js"></script>
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
<!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries -->
<!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
<!--[if lt IE 9]>
<script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
<script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
<![endif]-->







 


<script>
  $(function () {
      $('[data-toggle="tooltip"]').tooltip()
  })
</script>








  </head>

<body>

   <!-- Navigation -->
<nav class="navbar navbar-inverse navbar-fixed-top" role="navigation">
    <div class="container topnavlinks">
        <div class="navbar-header">
            <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
                <span class="sr-only">Toggle navigation</span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
            </button>
           
            <a class="fa fa-home fa-lg navbar-brand" href="index.html">&nbsp;<span class="projectTitle"> Stanford CoreNLP</span></a>
            
        </div>
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
            <ul class="nav navbar-nav navbar-right">
                <!-- entries without drop-downs appear here -->
                <!-- conditional logic to control which topnav appears for the audience defined in the configuration file.-->
                




                
                
                
                
                <li><a href="https://github.com/stanfordnlp/CoreNLP" target="_blank">Github repo</a></li>
                
                
                
                


                <!-- entries with drop-downs appear here -->
                <!-- conditional logic to control which topnav appears for the audience defined in the configuration file.-->

                <li class="dropdown">
                    
                    
                    
                    <a href="#" class="dropdown-toggle" data-toggle="dropdown">Quick links<b class="caret"></b></a>
                    <ul class="dropdown-menu">
                        
                        
                        
                        <li><a href="http://corenlp.run/" target="_blank">Online demo (Webservice API)</a></li>
                        
                        
                        
                        
                        
                        <li><a href="http://nlp.stanford.edu:8080/corenlp/" target="_blank">Online demo (Traditional)</a></li>
                        
                        
                        
                        
                        
                        <li><a href="http://mvnrepository.com/artifact/edu.stanford.nlp/stanford-corenlp" target="_blank">Maven Central</a></li>
                        
                        
                        
                        
                        
                        <li><a href="https://www.nuget.org/packages/Stanford.NLP.CoreNLP/" target="_blank">NuGet (.NET)</a></li>
                        
                        
                        
                        
                        
                        <li><a href="other-languages.html">Other languages/packages</a></li>
                        
                        
                        
                        
                        
                        <li><a href="http://www.anthology.aclweb.org/P/P14/P14-5010.pdf" target="_blank">Paper to cite</a></li>
                        
                        
                        
                        
                        
                        <li><a href="http://stackoverflow.com/questions/tagged/stanford-nlp" target="_blank">Stack Overflow</a></li>
                        
                        
                        
                        
                        
                        <li><a href="https://twitter.com/stanfordnlp" target="_blank">Twitter</a></li>
                        
                        
                        
                        

                    </ul>
                </li>
                
                


                <!-- special insertion -->

               
           
        </div>
        <!-- /.container -->
</nav>



    <!-- Page Content -->
    <div class="container">
        <div class="col-lg-12">&nbsp;</div>


<!-- Content Row -->
<div class="row">
<!-- Sidebar Column -->
<div class="col-md-3">

<script>

$(document).ready(function() {
// Initialize navgoco with default options
$("#mysidebar").navgoco({
caretHtml: '',
accordion: true,
//accordion: true,
openClass: 'active', // open
save: true, // leave false or nav highlighting doesn't work right
cookie: {
name: 'navgoco',
expires: false,
path: '/'
},
slide: {
duration: 000,
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







<ul id="mysidebar" class="nav">

<div class="siteTagline">CoreNLP</div>
<div class="versionTagline">version 3.9.1</div>


	

		

			<li><a href="#">Overview</a>
			
				<ul>
			

			
				
				
					
						<li><a href="index.html">About</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="index.html#download">Download</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="index.html#human-languages-supported">Languages</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="index.html#license">License and Citing</a></li>
					

					
					</li>
				
			
			
				</ul>
			
			</li>
		
	

		

			<li><a href="#">Usage</a>
			
				<ul>
			

			
				
				
					
						<li><a href="download.html">Download / Maven</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="migration.html">Migration Guide</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="cmdline.html">Command line usage</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="api.html">Stanford CoreNLP API</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="simple.html">Simple CoreNLP API</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="repl.html">Interactive mode (REPL)</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="corenlp-server.html">CoreNLP server</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="caseless.html">Caseless operation</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="human-languages.html">On other human languages</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="other-languages.html">From other languages/packages</a></li>
					

					
					</li>
				
			
			
				</ul>
			
			</li>
		
	

		

			<li><a href="#">Annotators</a>
			
				<ul>
			

			
				
				
					
						<li><a href="annotators.html">Summary</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="dependencies.html">Annotator dependencies</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="tokenize.html">Tokenization</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="ssplit.html">Sentence Splitting</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="lemma.html">Lemmatization</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="pos.html">Parts of Speech</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="ner.html">Named Entity Recognition</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="regexner.html">RegexNER (Named Entity Recognition)</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="parse.html">Constituency Parsing</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="depparse.html">Dependency Parsing</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="coref.html">Coreference Resolution</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="natlog.html">Natural Logic</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="openie.html">Open Information Extraction</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="sentiment.html">Sentiment</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="relation.html">Relation Extraction</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="quote.html">Quote Annotator</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="cleanxml.html">CleanXML Annotator</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="truecase.html">True case Annotator</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="entitymentions.html">Entity Mentions Annotator</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="udfeats.html">UD Features</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="new_annotator.html">Adding a new annotator</a></li>
					

					
					</li>
				
			
			
				</ul>
			
			</li>
		
	

		

			<li><a href="#">Additional tools</a>
			
				<ul>
			

			
				
				
					
						<li><a href="tokensregex.html">TokensRegex</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="patterns.html">Bootstrapped surface patterns</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="extensions.html">Extensions</a></li>
					

					
					</li>
				
			
			
				</ul>
			
			</li>
		
	

		

			<li><a href="#">Resources</a>
			
				<ul>
			

			
				
				
					
						<li><a href="faq.html">FAQ</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="tutorials.html">Tutorials</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="memory-time.html">Memory and time optimization</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="pipelines.html">Annotation pipelines</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="http://corenlp.run/" target="_blank">Online demo (API)</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="http://nlp.stanford.edu:8080/corenlp/" target="_blank">Online demo (old skool)</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="http://nlp.stanford.edu/nlp/javadoc/javanlp/" target="_blank">Javadoc</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="history.html">Release history</a></li>
					

					
					</li>
				
			
				
				
					
						<li><a href="contact.html">Contact</a></li>
					

					
					</li>
				
			
			
				</ul>
			
			</li>
		
	

</ul>


</div>
<!-- this highlights the active parent class in the navgoco sidebar. this is critical so that the parent expands when you're viewing a page. This must appear below the sidebar code above.-->
<script>$("li.active").parents('li').toggleClass("active");</script>


            <!-- Content Column -->
            <div class="col-md-9">

                <div class="post-header">
   <h1 class="post-title-main">POSTaggerAnnotator</h1>
</div>

<div class="post-content">

   

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


  <h2 id="description">Description</h2>

<p>Labels tokens with their POS tag. For more details see <a href="http://nlp.stanford.edu/software/tagger.html">this page</a>.</p>

<table>
  <thead>
    <tr>
      <th>Property name</th>
      <th>Annotator class name</th>
      <th>Generated Annotation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>pos</td>
      <td>POSTaggerAnnotator</td>
      <td>PartOfSpeechAnnotation</td>
    </tr>
  </tbody>
</table>

<h2 id="options">Options</h2>

<ul>
  <li>pos.model: POS model to use. There is no need to explicitly set this option, unless you want to use a different POS model (for advanced developers only). By default, this is set to the english left3words POS model included in the stanford-corenlp-models JAR file.</li>
  <li>pos.maxlen: Maximum sentence size for the POS sequence tagger.  Useful to control the speed of the tagger on noisy text without punctuation marks.  Note that the parser, if used, will be much more expensive than the tagger.</li>
</ul>

<h2 id="caseless-models">Caseless models</h2>

<p>It is possible to run StanfordCoreNLP with a POS tagger
model that ignores capitalization. We have trained models like this
for English. You can find details on the
<a href="caseless.html">Caseless models</a> page.</p>

<h2 id="more-information">More information</h2>

<p>The POS tagger is described in detail on the Stanford NLP <a href="http://nlp.stanford.edu/software/tagger.html">website</a>.</p>






















































































































































<div class="tags">
    
</div>



</div>

<hr class="shaded"/> 

<footer>
</footer>

            </div><!-- /.row -->

    </div>    <!-- /.container -->

</body>


</html>

