<!DOCTYPE html>
<html>
<!--Liliya Yerassilova
    Introduction to Programming
	Project 2 - Game v-0.2-->
	
    <head>
        <meta http-equiv="content-type" content="text/html;charset=utf-8"/>
        <meta name="keywords"           content="game, version 0.2"/>
        <meta name="author"             content="Liliya Yerassilova"/> 
        <title>Game</title>
	  
	    <script type="text/javascript">
	        var curLoc = 0;
			var score = 0;
			var navigationErrorCount = 0;
						
		    var hasVisitedRoom0 = false;
		    var hasVisitedRoom1 = false;
		    var hasVisitedRoom2 = false;
		    var hasVisitedRoom3 = false;
		    var hasVisitedRoom4 = false;
		    
			
		   //initial function
		   function init() {
		        dispmsg();
			}
		   
		   //navigation functions
		   function btn_go_North() {
		    if (curLoc === 3) {
			    curLoc = 0;	
                dispmsg();				
			   } else {
			       if (curLoc === 0) {
				       curLoc = 1;	
                       dispmsg();					   
			        } else {
					   navigationError();
					 }
			    }               				 
		   }
		 
		    function btn_go_South() {
			    if (curLoc === 1) {
			        curLoc = 0;	
                    dispmsg();					
			     } else {
			          if (curLoc === 0) {
				         curLoc = 3;
                         dispmsg();						 
				     } else {
					   navigationError();
					 }					  
		          }				
		    }
		    
		    function btn_go_West() {
		      if (curLoc === 4) {
                  curLoc = 0;  
                  dispmsg();				  
			      } else {
			           if (curLoc === 0) {
				           curLoc = 2;	
                            dispmsg();						   
				        } else {
					   navigationError();
					 }									
		         }				
	      } 
	      
		  function btn_go_East(){
		     if (curLoc === 2) {
			     curLoc = 0;
                 dispmsg();				 
			     } else {
			          if (curLoc === 0) {
			              curLoc = 4;
                          dispmsg();				          
			              } else {
					   navigationError();
					 }
		          }				  
		    }
			
		  function btnGo_click() {		      
			  if (txtCommand.value === "North" ||  "north" ||  "N" ||  "n") {
			      btn_go_North();			  
			  } else {
			      if (txtCommand.value === "South" ||  "south" ||  "S" ||  "s") {
				      btn_go_South();
					  } else {
					      if (txtCommand.value === "East" ||  "east" ||  "E" ||  "e") {
						      btn_go_East();
						 } else {
						     if (txtCommand.value === "West" ||  "west" ||  "W" ||  "w") {
							    btn_go_West();
								}
							}
					   }
			   }
		}
		  
		  //story function
		  function dispmsg() {
		            checkScore();
		            dspScore();
		            var message = "";
                    switch(curLoc) {
                        case 0: message = "room 0";
                                break;
                        case 1: message = "room 1";
                                break;
                        case 2: message = "room	2";
                                break;
                        case 3: message = "room 3";
                                break;
                        case 4: message = "room 4";
                                break;
                        default: message = "You cannot go this way.";
                    }
				presentMessage(message);	
		  }
		  
		  function navigationError() {
		        navigationErrorCount = navigationErrorCount + 1;		    
			    presentMessage("You cannot go that way.");		     		 
		  }
		  
		  //utility function
		  function presentMessage(message) {
			   var target = document.getElementById("mainText");
               target.value = message + "\n\n" + target.value;
            }	
			
		  // functions for keeping and showing score!
		  function checkScore() {
		     if (curLoc === 0) {
		         if (! hasVisitedRoom0) {	        
			         score = score + 5;
				     hasVisitedRoom0 = true;
				    }
		     }
		     
		     if (curLoc === 1) {			
			      if (! hasVisitedRoom1) {			  
			          score = score + 5;
				      hasVisitedRoom1 = true;
				   }
				 }
				 
								 		
			  if (curLoc === 2) {
			     if (! hasVisitedRoom2) {
			         score = score + 5;
				     hasVisitedRoom2 = true;
				   }
				}
				   
				   
			if (curLoc === 3) {
				  if (! hasVisitedRoom3) {
			          score = score + 5;
				      hasVisitedRoom3 = true;
			}
			   }
				 
			if (curLoc === 4) {
			    if (! hasVisitedRoom4) {
			        score = score + 5;
				    hasVisitedRoom4 = true;				 
			}
			   }
			     }
			     			
			function dspScore() {			         
					     document.getElementById("scoreText").value = "Score:" + score;
			}
						
	   </script>	 
       <style>
	       div {position: absolute;
		          top: 140px;
			        left: 465px;
			    }
	   </style>     	  
  </head>
    <body onload="init();">
        <h1>
	       Inside a Mansion
	    </h1>
	    <br>
	       If you want to write to me:
                  <a href="mailto:liliya-er@mail.ru?Subject=My%20message">
                      Click here</a>
	   <br><br>
	   <textarea rows="15" cols="50" id="mainText"></textarea>
     <div id="scorebox">
          <textarea rows="5" cols="8" id="scoreText"></textarea>	
	 </div>
	 <br><br>
	 Your Command:
	    <input type="text"
		       id="txtCommand"
			   name="txtCommand">
			   
	    <input type="button"
		       value="Go"
			   onclick="btnGo_click();"/>
			   
		<br><br>
	    <input type="button"
	           value="North"
		       onclick="btn_go_North();" />

       <input type="button"
	          value="South"
		      onclick="btn_go_South();" />

       <input type="button"
	          value="West"
		      onclick="btn_go_West();" />

       <input type="button"
	          value="East"
		      onclick="btn_go_East();" />
 
   </body>  
</html>


