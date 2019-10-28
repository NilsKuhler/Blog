
{% assign selectedcourse = include.selectedcourse | strip %}
{% assign coursefound = false %}
{% assign matchfirst = false %}


{% if selectedcourse %}
	{% for course in site.data.courses.allcourses %}
	    {% if course.courseid == selectedcourse %}
		    {% assign coursefound = true %}
			{% assign courseid= course.courseid %}
			{% assign coursename = course.course %}
		    {% assign courseid = course.courseid %}
		    {% assign coursedate = course.date %}
		    {% assign courseinst1 = course.institution1 %}
		    {% assign courseinst2 = course.institution2 %}
		    {% assign coursegrade = course.grade %}
		    {% assign coursecomment = course.comment %}
		    {% assign courseurl = course.url_course %}
		    {% assign coursemyurl = course.myurl_course %}
		    {% assign coursemyurlresult = course.myurl_result %}
			{% assign course_summary = course.summary %}
	        {% break %}		
	    {% endif %}
	{% endfor %}
{% endif %}

<p>
{% if coursefound %}
    <table width="70%" class="display">
	<thead><tr><th><center>--- Course details overview ---</center></th></tr></thead>
	    <tr><th>MyCourseID & Course Name</th></tr>
	    <tr><td> {{ courseid }} - {{ coursename }} </td></tr>
	    <tr ><th>Course Provider / Institution</th></tr>
		{% if courseinst2 %}
		{% assign courseinst_str = courseinst1 | append : " by " | append : courseinst2 %}
		{% else %}	
		{% assign courseinst_str = courseinst1 %}		
		{% endif %}		
		<tr ><td> {{ courseinst_str }} </td></tr>
	    <tr ><th>Date completed & Result</th></tr>
		<tr ><td> {{ coursedate }} {{ coursegrade | prepend : "Result:"}} </td></tr>
		<tr ><th>Link - Course Description-provider</th></tr>
		{% if courseurl %}
			{% capture hrefstr %}<a href="{{ courseurl }}">{{ courseurl }}</a>{% endcapture %}
			<tr><td> {{ hrefstr }} </td></tr>
		{% else %}	
				<tr><td> No course description link available </td></tr>		
		{% endif %}
		        <tr><th>Link - course result(s) e.g. github</th></tr>
		{% if coursemyurlresult %}
	        {% capture hrefstr %}<a href="{{ coursemyurlresult }}">{{ coursemyurlresult }}</a>{% endcapture %}
			    <tr><td> {{ hrefstr }} </td></tr>
		{% else %}	
				<tr><td> No course result link available </td></tr>	
		{% endif %}	
		        <tr><th>Link - My blog course comments/summary on course</th></tr>
		{% if coursemyurl %}
		    {% capture hrefstr %}<a href="{{ coursemyurl }}">{{ coursemyurl }}</a>{% endcapture %}
			    <tr><td> {{ hrefstr }} </td></tr>
		{% else %}
			    <tr><td> No course blog course comments/summary available </td></tr>
		{% endif %}
		        <tr><th>Short inline summary on course</th></tr>		
		{% if course_summary %}
			    <tr><td> {{ course_summary }} </td></tr>
		{% else %}
			    <tr><td> No summary available </td></tr>
		{% endif %}
		        <thead><tr><th><center>--- End course details overview ---</center></th></tr></thead>
				
	    </table>
{% else %}
    <table width="70%" class="display">  
		<thead><tr><th>Could not find the course id</th></tr></thead>
		<tbody><tr><td> An error occurred please contact site administrator </td></tr></tbody>
	</table>
{% endif %}
</p>
