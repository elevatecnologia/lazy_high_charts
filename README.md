LazyHighCharts
==============

##plugin for make highcharts a la ruby

  highcharts:http://www.highcharts.com/demo/

Some Ideas & code taken from 

  flotomatic

  open_flash_chart_lazy

##requires:
  
  jquery (it not conflics with prototype)
  
  tested in rails 2.3.x and 3.0.0
  

Usage
=======

 Usage in Controller:
  
     @h = HighChart.new('graph') do |f|
<<<<<<< HEAD
        f.series(:name=>'John', :data=>[3, 20, 3, 5, 4, 10, 12 ,3, 5,6,7,7,80,9,9])
        f.series(:name=>'Jane', :data=> [1, 3, 4, 3, 3, 5, 4,-46,7,8,8,9,9,0,0,9] )
=======
        f.series('John', [3, 20, 3, 5, 4, 10, 12 ,3, 5,6,7,7,80,9,9])
        f.series('Jane', [1, 3, 4, 3, 3, 5, 4,-46,7,8,8,9,9,0,0,9] )
>>>>>>> fab1debcf6951aed0147e2578bb71b4265ef2058
      end
 

  Without overriding entire option , (only change a specific option index):  
 
     @h = HighChart.new('graph') do |f|
      .....
          f.options[:chart][:defaultSeriesType] = "area"
          f.options[:chart][:inverted] = true
          f.options[:legend][:layout] = "horizontal"
          f.options[:x_axis][:categories] = ["uno" ,"dos" , "tres" , "cuatro"]
     ......

  Overriding entire option: 

     @h = HighChart.new('graph') do |f|
       .....
          f.x_axis(:categories => @days.reverse! , :labels=>{:rotation=>-45 , :align => 'right'})
          f.chart({:defaultSeriesType=>"spline" , :renderTo => "myRenderArea" , :inverted => true})
       .....


  Usage in layout:
      
     <%= javascript_include_tag :defaults %>
     <%= javascript_include_tag :high_charts %>
     <!--[if IE]>
      <%= javascript_include_tag :ie_high_charts %>
     <![endif]-->
      
  Usage in view:
  
    <%= high_chart("my_id", @h) %>
    
  Passing formatting options in the view to the helper block , because all the helper options declared in the controller are converted in strict/valid json (quoted key);  so we need to extend the json object with some js.
  
      <% high_chart("my_id", @h) do |c| %>
         	<%= "options.tooltip.formatter = function() { return '<b>HEY!!!'+ this.series.name +'</b><br/>'+ this.x +': '+ this.y +' units';}" %>
         	<%= "options.xAxis.labels.formatter = function() { return 'ho';}" %>
         	<%= "options.yAxis.labels.formatter = function() { return 'hey';}" %>
       <%end %> 
      


  Option reference:

     http://www.highcharts.com/ref/
    


Copyright (c) 2009 [Miguel Michelson Martinez], released under the MIT license
