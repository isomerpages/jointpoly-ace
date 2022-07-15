---
title: FAQ
permalink: /faq/
---
## FAQ

#### 1. I am interested in signing up for a Joint Polytechnic Programme. How do I register? 

Enrolment for the four Joint Polytechnic Programmes are currently through respective polytechnic's nomination. The joint polytechnic programmes are not open to members of the public at this moment. Polytechnic staff who are keen to be considered for the programmes may contact respective polytechnic coordinators for each programme. 

#### 2. I am a polytechnic staff and I have a question regarding Joint Polytechnic programmes. Is there someone whom I can contact if I have an enquiry? 

You may contact any JP-AcE colleagues, your Programme Head or your respective Polytechnic Coordinators if you need urgent assistance with regards to the joint polytechnic programmes. The contacts can be found on each programme page on this website.



#### 3. I am an adult educator from private sector. Is there any learning opportunities available on JP-AcE that might be suitable for me?

Thank you for visiting the site. JP-AcE drives T&L capability development for adult educators. Adult educators who are interested to upskill Teaching and Learning capabilities may explore the website under Programmes>Adult Education for more information.

---
layout: page
---

{%- if content contains '<hr />' -%}
	{%- assign sections = content | split: '<hr />' -%}
{%- elsif content contains '<hr/>' -%}
	{%- assign sections = content | split: '<hr/>' -%}
{%- else -%}
	{%- assign sections = content -%}
{%- endif -%}

{%- for section in sections -%}
<div style="margin-bottom: 3rem;">
	{%- assign list = section | split: '<h' -%}
	{%- for listitem in list -%}
		{%- if listitem contains 'id="qn' or item contains "id='qn" -%}
			{%- assign arr = listitem | split: '</h' -%}
			{%- for item in arr -%}	
				{%- if forloop.first == true -%}
					{%- assign questionHeaderLevel = item | slice: 0 -%}
					{%- assign questionHeaderBackTagPartial = questionHeaderLevel | append: '>' -%}
					{%- assign questionHeaderBackTag = questionHeaderBackTagPartial | prepend: '</h' -%}	
					{%- assign question = item | prepend: '<h' | append: questionHeaderBackTag -%}
					{%- comment -%} Accordion header {%- endcomment -%}
					<div class="col is-large bp-accordion-header padding has-icons-right field has-addons is-marginless">
						<div class="col is-expanded is-fullwidth is-paddingless">
							<h5 class="has-text-grey-dark is-marginless">
								<b style="cursor:default;">{{- question | strip_html -}}</b>
							</h5>
						</div>
						<span class="sgds-icon sgds-icon-plus is-size-4 bp-accordion-button"></span>
					</div>	
				{%- else -%}
					{%- assign answer = item | remove_first: questionHeaderBackTagPartial -%}
					{%- comment -%} Accordion body {%- endcomment -%}
					<div id="accordion-body-{% increment counter %}" class="col padding bp-accordion-body">
						<div class="bp-container is-full padding--top--lg padding--bottom" style="width: 100%">	
							{{- answer -}}
						</div>
					</div>	
				{%- endif -%}
			{%- endfor -%}
		{%- else -%}
			{%- if listitem contains '</h' -%}			
				<h{{- listitem -}}
			{%- endif -%}		
		{%- endif -%}
	{%- endfor -%}
</div>	
{%- endfor -%}

<script src="assets/js/accordion.js"></script>
