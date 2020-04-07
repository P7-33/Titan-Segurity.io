---
title: 'Add A Pop Posts Gallery Merely Higher Upward Your Blogger Posts'
date: 2020-02-08T06:39:00+01:00
draft: false
---

The nearly pop spider web pattern tendency over concluding duo of years are horizontal sliding panels, likewise known equally sliders or carousels. One of the effective ways to growth the site usability too engage the user is to add together a pop posts gallery higher upward Blogger posts to display the nearly viewed 10 posts on your blog.  
  
To run into it live, delight see the demo spider web log below.  
  

[![](https://4.bp.blogspot.com/-teBazFNbCj0/T4GfmIXWryI/AAAAAAAABtA/LEdOf2yC3D0/s1600/add+a+popular+posts+gallery+widget+above+blogger+blogspot+posts.png)](http://4.bp.blogspot.com/-teBazFNbCj0/T4GfmIXWryI/AAAAAAAABtA/LEdOf2yC3D0/s1600/add+a+popular+posts+gallery+widget+above+blogger+blogspot+posts.png)

![](https://1.bp.blogspot.com/-PUc68N15qEw/T4GXUZBOc8I/AAAAAAAABs4/3PMg7YWreR0/s640/popular+posts+blogger+blogspot+widget+with+jQuery+effect.png)

  

[Demo blog](http://popular-posts-blogger-widget.blogspot.com/)

  

Adding Popular Posts Gallery Above Blogger Posts
------------------------------------------------

Before adding the [Popular posts widget](https://rdbrry.blogspot.com//search?q=5-popular-posts-widget-for-blogger) equally gallery inward Blogger, delight banknote that this widget is non fully compatible amongst all templates, hence it's recommended to brand a backup earlier making whatever changes inward your Blogger template.  
  
Now, follow these steps:  
  
1\. Go to Dashboard, click "Template" > hitting the "Edit HTML" clitoris too click anywhere within the code expanse > press the CTRL + F keys to opened upward the Blogger search box.  
  
2\. Type or glue this tag within the search box:  

> \]\]>

Note: you lot may convey to click the arrow adjacent to it, hence drive to uncovering \]\]> again.  
  
3\. Just above/before it, add together the next CSS:  

> #gallery{position:relative;margin:0 0 20px;height:126px;}  
> #gallery .belt{position:absolute;top:0;left:0;list-style-type:none}  
> #gallery .panel{float:left;margin:0px 10px 20px 0;width:84px;height:86px;background:url(http://2.bp.blogspot.com/-\_Srvna\_zg0M/T393\_LXqDLI/AAAAAAAABrQ/\_t2GmPexCHo/s1600/bg-slider.png) bottom pump no-repeat;overflow:hidden}  
> #gallery .panel img{border:1px corporation #DDD;margin:7px 6px 6px;width:72px;height:72px;background:#FFF;padding:0px}

Note: modify the value inward reddish (126px) to conform the gallery height.  
  
4\. Now search the next tag:  

5\. Just above/before it, add together the script for the Popular Posts gallery too jQuery:  

> <script type='text/javascript'><br /> //<!\[CDATA\[<br /> var stepcarousel={ajaxloadingmsg:'<div style="margin: 1em; font-weight: bold"><img src="ajaxloadr.gif" style="vertical-align: middle" /> Fetching Content. Please wait...</div>',defaultbuttonsfade:0.4,configholder:{},getCSSValue:function(val){return(val=="auto")?0:parseInt(val)},getremotepanels:function($,config){config.$belt.html(this.ajaxloadingmsg)<br /> $.ajax({url:config.contenttype\[1\],async:true,error:function(ajaxrequest){config.$belt.html('Error fetching content.<br />Server Response: '+ajaxrequest.responseText)},success:function(content){config.$belt.html(content)<br /> config.$panels=config.$gallery.find('.'+config.panelclass)<br /> stepcarousel.alignpanels($,config)}})},getoffset:function(what,offsettype){return(what.offsetParent)?what\[offsettype\]+this.getoffset(what.offsetParent,offsettype):what\[offsettype\]},getCookie:function(Name){var re=new RegExp(Name+"=\[^;\]+","i");if(document.cookie.match(re))<br /> provide document.cookie.match(re)\[0\].split("=")\[1\]<br /> provide null},setCookie:function(name,value){document.cookie=name+"="+value},fadebuttons:function(config,currentpanel){config.$leftnavbutton.fadeTo('fast',currentpanel==0?this.defaultbuttonsfade:1)<br /> config.$rightnavbutton.fadeTo('fast',currentpanel==config.lastvisiblepanel?this.defaultbuttonsfade:1)},addnavbuttons:function(config,currentpanel){config.$leftnavbutton=jQuery('<img src="'+config.defaultbuttons.leftnav\[0\]+'">').css({zIndex:50,position:'absolute',left:config.offsets.left+config.defaultbuttons.leftnav\[1\]+'px',top:config.offsets.top+config.defaultbuttons.leftnav\[2\]+'px',cursor:'hand',cursor:'pointer'}).attr({title:'Back '+config.defaultbuttons.moveby+' panels'}).appendTo('body')<br /> config.$rightnavbutton=jQuery('<img src="'+config.defaultbuttons.rightnav\[0\]+'">').css({zIndex:50,position:'absolute',left:config.offsets.left+config.$gallery.get(0).offsetWidth+config.defaultbuttons.rightnav\[1\]+'px',top:config.offsets.top+config.defaultbuttons.rightnav\[2\]+'px',cursor:'hand',cursor:'pointer'}).attr({title:'Forward '+config.defaultbuttons.moveby+' panels'}).appendTo('body')<br /> config.$leftnavbutton.bind('click',function(){stepcarousel.stepBy(config.galleryid,-config.defaultbuttons.moveby)})<br /> config.$rightnavbutton.bind('click',function(){stepcarousel.stepBy(config.galleryid,config.defaultbuttons.moveby)})<br /> if(config.panelbehavior.wraparound==false){this.fadebuttons(config,currentpanel)}<br /> provide config.$leftnavbutton.add(config.$rightnavbutton)},stopautostep:function(config){clearTimeout(config.steptimer)<br /> clearTimeout(config.resumeautostep)},alignpanels:function($,config){var paneloffset=0<br /> config.paneloffsets=\[paneloffset\]<br /> config.panelwidths=\[\]<br /> config.$panels.each(function(index){var $currentpanel=$(this)<br /> $currentpanel.css({float:'none',position:'absolute',left:paneloffset+'px'})<br /> $currentpanel.bind('click',function(e){return config.onpanelclick(e.target)})<br /> paneloffset+=stepcarousel.getCSSValue($currentpanel.css('marginRight'))+parseInt($currentpanel.get(0).offsetWidth||$currentpanel.css('width'))<br /> config.paneloffsets.push(paneloffset)<br /> config.panelwidths.push(paneloffset-config.paneloffsets\[config.paneloffsets.length-2\])})<br /> config.paneloffsets.pop()<br /> var addpanelwidths=0<br /> var lastpanelindex=config.$panels.length-1<br /> config.lastvisiblepanel=lastpanelindex<br /> for(var i=config.$panels.length-1;i>=0;i--){addpanelwidths+=(i==lastpanelindex?config.panelwidths\[lastpanelindex\]:config.paneloffsets\[i+1\]-config.paneloffsets\[i\])<br /> if(config.gallerywidth>addpanelwidths){config.lastvisiblepanel=i}}<br /> config.$belt.css({width:paneloffset+'px'})<br /> config.currentpanel=(config.panelbehavior.persist)?parseInt(this.getCookie(window\[config.galleryid+"persist"\])):0<br /> config.currentpanel=(typeof config.currentpanel=="number"&&config.currentpanel<config.$panels.length)?config.currentpanel:0<br /> if(config.currentpanel!=0){var endpoint=config.paneloffsets\[config.currentpanel\]+(config.currentpanel==0?0:config.beltoffset)<br /> config.$belt.css({left:-endpoint+'px'})}<br /> if(config.defaultbuttons.enable==true){var $navbuttons=this.addnavbuttons(config,config.currentpanel)<br /> $(window).bind("load resize",function(){config.offsets={left:stepcarousel.getoffset(config.$gallery.get(0),"offsetLeft"),top:stepcarousel.getoffset(config.$gallery.get(0),"offsetTop")}<br /> config.$leftnavbutton.css({left:config.offsets.left+config.defaultbuttons.leftnav\[1\]+'px',top:config.offsets.top+config.defaultbuttons.leftnav\[2\]+'px'})<br /> config.$rightnavbutton.css({left:config.offsets.left+config.$gallery.get(0).offsetWidth+config.defaultbuttons.rightnav\[1\]+'px',top:config.offsets.top+config.defaultbuttons.rightnav\[2\]+'px'})})}<br /> if(config.autostep&&config.autostep.enable){var $carouselparts=config.$gallery.add(typeof $navbuttons!="undefined"?$navbuttons:null)<br /> $carouselparts.bind('click',function(){stepcarousel.stopautostep(config)<br /> config.autostep.status="stopped"})<br /> $carouselparts.hover(function(){stepcarousel.stopautostep(config)<br /> config.autostep.hoverstate="over"},function(){if(config.steptimer&&config.autostep.hoverstate=="over"&&config.autostep.status!="stopped"){config.resumeautostep=setTimeout(function(){stepcarousel.autorotate(config.galleryid)<br /> config.autostep.hoverstate="out"},500)}})<br /> config.steptimer=setTimeout(function(){stepcarousel.autorotate(config.galleryid)},config.autostep.pause)}<br /> this.statusreport(config.galleryid)<br /> config.oninit()<br /> config.onslideaction(this)},stepTo:function(galleryid,pindex){var config=stepcarousel.configholder\[galleryid\]<br /> if(typeof config=="undefined"){alert("There's an fault amongst your gear upward of Carousel Viewer \\""+galleryid+"\\"!")<br /> return}<br /> stepcarousel.stopautostep(config)<br /> var pindex=Math.min(pindex-1,config.paneloffsets.length-1)<br /> var endpoint=config.paneloffsets\[pindex\]+(pindex==0?0:config.beltoffset)<br /> if(config.panelbehavior.wraparound==false&&config.defaultbuttons.enable==true){this.fadebuttons(config,pindex)}<br /> config.$belt.animate({left:-endpoint+'px'},config.panelbehavior.speed,function(){config.onslideaction(this)})<br /> config.currentpanel=pindex<br /> this.statusreport(galleryid)},stepBy:function(galleryid,steps){var config=stepcarousel.configholder\[galleryid\]<br /> if(typeof config=="undefined"){alert("There's an fault amongst your gear upward of Carousel Viewer \\""+galleryid+"\\"!")<br /> return}<br /> stepcarousel.stopautostep(config)<br /> var direction=(steps>0)?'forward':'back'<br /> var pindex=config.currentpanel+steps<br /> if(config.panelbehavior.wraparound==false){pindex=(direction=="back"&&pindex<=0)?0:(direction=="forward")?Math.min(pindex,config.lastvisiblepanel):pindex<br /> if(config.defaultbuttons.enable==true){stepcarousel.fadebuttons(config,pindex)}}<br /> else{if(pindex>config.lastvisiblepanel&&direction=="forward"){pindex=(config.currentpanel<config.lastvisiblepanel)?config.lastvisiblepanel:0}<br /> else if(pindex<0&&direction=="back"){pindex=(config.currentpanel>0)?0:config.lastvisiblepanel}}<br /> var endpoint=config.paneloffsets\[pindex\]+(pindex==0?0:config.beltoffset)<br /> if(pindex==0&&direction=='forward'||config.currentpanel==0&&direction=='back'&&config.panelbehavior.wraparound==true){config.$belt.animate({left:-config.paneloffsets\[config.currentpanel\]-(direction=='forward'?100:-30)+'px'},'normal',function(){config.$belt.animate({left:-endpoint+'px'},config.panelbehavior.speed,function(){config.onslideaction(this)})})}<br /> else<br /> config.$belt.animate({left:-endpoint+'px'},config.panelbehavior.speed,function(){config.onslideaction(this)})<br /> config.currentpanel=pindex<br /> this.statusreport(galleryid)},autorotate:function(galleryid){var config=stepcarousel.configholder\[galleryid\]<br /> if(config.$gallery.attr('\_ismouseover')!="yes"){this.stepBy(galleryid,config.autostep.moveby)}<br /> config.steptimer=setTimeout(function(){stepcarousel.autorotate(galleryid)},config.autostep.pause)},statusreport:function(galleryid){var config=stepcarousel.configholder\[galleryid\]<br /> var startpoint=config.currentpanel<br /> var visiblewidth=0<br /> for(var endpoint=startpoint;endpoint<config.paneloffsets.length;endpoint++){visiblewidth+=config.panelwidths\[endpoint\]<br /> if(visiblewidth>config.gallerywidth){break}}<br /> startpoint+=1<br /> endpoint=(endpoint+1==startpoint)?startpoint:endpoint<br /> var valuearray=\[startpoint,endpoint,config.panelwidths.length\]<br /> for(var i=0;i<config.statusvars.length;i++){window\[config.statusvars\[i\]\]=valuearray\[i\]<br /> config.$statusobjs\[i\].text(valuearray\[i\]+" ")}},setup:function(config){document.write('<style type="text/css">\\n#'+config.galleryid+'{overflow: hidden;}\\n</style>')<br /> jQuery(document).ready(function($){config.$gallery=$('#'+config.galleryid)<br /> config.gallerywidth=config.$gallery.width()<br /> config.offsets={left:stepcarousel.getoffset(config.$gallery.get(0),"offsetLeft"),top:stepcarousel.getoffset(config.$gallery.get(0),"offsetTop")}<br /> config.$belt=config.$gallery.find('.'+config.beltclass)<br /> config.$panels=config.$gallery.find('.'+config.panelclass)<br /> config.panelbehavior.wraparound=(config.autostep&&config.autostep.enable)?true:config.panelbehavior.wraparound<br /> config.onpanelclick=(typeof config.onpanelclick=="undefined")?function(target){}:config.onpanelclick<br /> config.onslideaction=(typeof config.onslide=="undefined")?function(){}:function(beltobj){$(beltobj).stop();config.onslide()}<br /> config.oninit=(typeof config.oninit=="undefined")?function(){}:config.oninit<br /> config.beltoffset=stepcarousel.getCSSValue(config.$belt.css('marginLeft'))<br /> config.statusvars=config.statusvars||\[\]<br /> config.$statusobjs=\[$('#'+config.statusvars\[0\]),$('#'+config.statusvars\[1\]),$('#'+config.statusvars\[2\])\]<br /> config.currentpanel=0<br /> stepcarousel.configholder\[config.galleryid\]=config<br /> if(config.contenttype\[0\]=="ajax"&&typeof config.contenttype\[1\]!="undefined")<br /> stepcarousel.getremotepanels($,config)<br /> else<br /> stepcarousel.alignpanels($,config)})<br /> jQuery(window).bind('unload',function(){if(config.panelbehavior.persist){stepcarousel.setCookie(window\[config.galleryid+"persist"\],config.currentpanel)}<br /> jQuery.each(config,function(ai,oi){oi=null})<br /> config=null})}}<br /> //\]\]><br />  
> <br /> //<!\[CDATA\[<br /> stepcarousel.setup({<br /> galleryid: "gallery",<br /> beltclass: "belt",<br /> panelclass: "panel",<br /> autostep: {enable:true, moveby:1, pause:5000},<br /> panelbehavior: {speed:800, wraparound:true, persist:true},<br /> defaultbuttons: {enable: true, moveby: 2, leftnav: \["http://2.bp.blogspot.com/-0Iss3Wjr36Q/T393U65TcKI/AAAAAAAABq4/K\_uzwyuNzrE/s1600/prev.png", -40, 25\], rightnav: \["http://1.bp.blogspot.com/-DtspeRHclnQ/T393WdyB8EI/AAAAAAAABrA/TKHickb2iI8/s1600/next.png", -10, 25\]},<br /> contenttype: \["external"\]<br /> })<br /> //\]\]><br />

Now that nosotros added the scripts to brand our gallery work, let's add together the HTML of the Popular Posts widget higher upward the Blogger posts.  
  
6\. Search this line:  

Note: If you lot can't uncovering it, search this one:  

7\. Just below it, add together the next code:  

>   
>   
>   
> 
>   
>  
> 
>   
>   
> 
>   
>      
>     *     
>            
>             
>              
>             
>            
>     
>       
>               
>            
>     
>       
>            
>     
>       
>               
>            
>     
>       
>             
>            
>             
>              
>                
>              
>              ![no image](http://2.bp.blogspot.com/-mRxY2oEkLJc/T393wpt0z_I/AAAAAAAABrI/4blMjDaSOUY/s1600/no-image.PNG)  
>              
>             
>            
>         
>   
>      
>   
> 
>   
>  
> 
>   
>    

Note: Delete the lines inward bluish if you lot desire this widget to live displayed inward posts pages, equally well.  
  
8\. Preview your template too if everything is OK, press the 'Save Template'.  Now you're done adding the Popular Posts Gallery! Just sentiment your spider web log too run into it alive higher upward the Blogger posts.