---
layout: post
title:  "All courses"
categories: 
tags:  
author: NK
mathjax: true
datatable: true
---

* content
{:toc}




## Design of this page

This blog page is currently a draft webpage. 
This blog item reads in all completed courses from file and will display them in a table. 

## My completed courses


<table width="70%" class="display">
   <thead>
	<tr width="70%">
		<th>Date</th>
		<th>Course Description </th>
		<th>Provider/Institution</th>
		<th>Comment</th>
	</tr>
   </thead>
   <tbody>   
{% assign row_index = 0 %}         <!--row index not used for the moment -->

	{% for course in site.data.courses.allcourses %}
    <tr width="70%">
    {% assign row_index = row_index | plus : 1 %}
	    <td> {{ course.date | slice : 0 , 4 }} </td> 
		<td> {{ course.course }} </td>
		<td> {{ course.institution1  }} </td>
   		<td> {{ course.institution1.Comment | append : course.grade }} </td>
    </tr>
	{% endfor %}
   </tbody>
</table>



