---
layout: empty
date: 2015-03-01 00:00:00 +0530
permalink: /atom.xml
---
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
	<title type="text">{{ site.title }}</title>
	<subtitle type="text">{{ site.tagline }}</subtitle>
	<id>{{ site.url }}{{ post.url }}/</id>
	<updated>{{ site.time | date_to_xmlschema }}</updated>
	<link rel="alternate" type="text/html" hreflang="en" href="{{ site.url }}"/>
	<link rel="self" type="application/atom+xml" href="{{ site.url }}/atom.xml"/>
	<!-- PubSubHubbub Discovery -->
	<link rel="hub" href="http://smileprem.superfeedr.com/" />
	<rights>{{site.copyright}}</rights>
	<author>
		<name>{{ site.author }}</name>
		<uri>{{ site.url }}/</uri>
		<email>{{ site.email }}</email>
	</author>
	<category term="blogs"/>

	{% for post in site.posts limit:10 %}
	<entry>
		<title>{{ post.title | xml_escape }}</title>
		<link rel="alternate" type="text/html" href="{{ site.url }}{{ post.url }}"/>
		<id>{{ site.url }}{{ post.url }}</id>
		<updated>{{ post.date | date_to_xmlschema }}</updated>
		<published>{{ post.date | date_to_xmlschema }}</published>
		<author>
		{% if post.author-name != null %}
			<name>{{ post.author-name }}</name>
			<uri>{{ post.author-site }}</uri>
			<email>{{ post.author-email }}</email>
		{% else %}
			<name>{{ site.author }}</name>
			<uri>{{ site.url }}</uri>
			<email>{{ site.email }}</email>
		{% endif %}
		</author>
		<category term="{{ post.category }}"/>
		<content type="html" xml:lang="en" xml:base="{{ site.url }}{{ post.url }}">{{ post.content | xml_escape }}</content>
	</entry>
	{% endfor %}
</feed>