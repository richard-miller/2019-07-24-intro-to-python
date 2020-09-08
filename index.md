---
layout: workshop                  # DON'T CHANGE THIS.
carpentry: "swc"                  # what kind of Carpentry (must be either "lc" or "dc" or "swc").  
                                  # Be sure to update the Carpentry type in _config.yml as well.  
venue: "Macquarie University"     # brief name of host site without address (e.g., "Euphoric State University")
address: "Manly Room, Level 4, 17 Wally's Walk (C5C), Macquarie University, Sydney NSW 2122"      
                                  # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: "au"                     # lowercase two-letter ISO country code eg "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes)
language: "en"                    # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
latlng: "-33.774858, 151.113265"  # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use https://www.latlong.net/)
humandate: "24-25 July 2019"      # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 am - 4:30 pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2019-07-24             # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2019-07-25               # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Richard Miller", "James Tocknell", "George Milunovich", "Nishen Naidoo", "Thomas Reichardt"] 
                                  # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings"]
helper: ["TBA"]                   # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas"]
email: ["richard.miller@mq.edu.au", "odette.subijano@mq.edu.au"]    
                                  # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:              # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
#eventbrite: "64224905421"                      # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% if page.carpentry != site.carpentry %}
<div class="alert alert-warning">
You specified <code>carpentry: {{page.carpentry}}</code> in <code>index.md</code> and
<code>carpentry: {{site.carpentry}}</code> in <code>_config.yml</code>. Make sure you edit both files. After editing <code>_config.yml</code>, you need to run <code>make serve</code> again to 
see the changes take effect locally.
</div>
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION
{% endcomment %}

{% include sc/intro.html %}


{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% include sc/who.html %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> Participants will need to bring a laptop with a
  macOS, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  They will need an internet browser installed (Chrome recommended).
  Participants must also sign-up for a <a href="https://github.com/">GitHub</a> account if they don't already have one.
</p>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<p id="code-of-conduct">
<strong>Code of Conduct:</strong>
Everyone who participates in Carpentries activities is required to conform to the 
<a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. 
This document also outlines how to report an incident if needed.
</p>


{% comment %}
ACCESSIBILITY
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop accessible to everybody.
  The workshop organisers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>

{% comment %}
CONTACT EMAIL ADDRESS
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% comment %} 
SURVEYS - DO NOT EDIT SURVEY LINKS 

<h2 id="surveys">Surveys</h2>
<p>Please complete these surveys before and after the workshop:</p>

<ul>
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
</ul>
{% endcomment %}

{% comment %}
SCHEDULE
{% endcomment %}
<h2 id="schedule">Schedule</h2>
{% include sc/schedule.html %}

{% comment %}
SYLLABUS

<h2 id="syllabus">Syllabus</h2>
{% include sc/syllabus.html %}
{% endcomment %}


{% comment %}
SETUP
{% endcomment %}

<h2 id="setup">Pre Workshop Setup</h2>
<p>
  Before attending the workshop, you will need to ensure you have:
  <ul>
    <li> A macOS, Windows or Linux laptop for use during the workshop. </li>
    <li> Internet access from your device - Macquarie OneNet Wifi and eduRoam are available in the venue. </li>
    <li> A <a href="https://github.com">GitHub account</a> - sign up is free. </li>
    <li> Completed the: <a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a> </li>
  </ul>
</p>

{% comment %}
Workshop Materials
{% endcomment %}
<h2>Workshop Materials</h2>

<p>
All the workshop materials are available in the follow in GitHub Repository:
<ul>
  <img src="https://img.icons8.com/color/48/000000/git.png">
  <a href="https://github.com/MQ-software-carpentry/2019-07-24-intro-to-python-workshop">https://github.com/MQ-software-carpentry/2019-07-24-intro-to-python-workshop</a>
</ul>

</p>

<br/>
<br/>
<br/>
<br/>
