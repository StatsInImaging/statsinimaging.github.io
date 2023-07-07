---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
permalink: /resources_jobs/
---

<script>
  function showFun(pID, pbnID) {
    var x = document.getElementById(pID);
    var bntext = document.getElementById(pbnID);
    if (x.style.display === "none") {
      x.style.display = "block";
      bntext.innerText = "Hide Description";
    } else {
      x.style.display = "none";
      bntext.innerText = "Show Description";
    }
  }
</script>

<p align=center>
<button class="buttonSI" name="button" style="height:20%;width:40%" onclick="window.location.href='https://docs.google.com/forms/d/e/1FAIpQLSc6m-k3GxXb_f6301shiAnjMfsn5kAImYFKh04SDrfJ1V9FWQ/viewform?usp=sf_link'"><font size="3">Post A Job</font></button>
</p>

{% for job in site.data.job_postings %}

<div class="jp"
  style="border: 1px solid black; margin: auto; margin-bottom: 15px; width: 100%; padding: 10px; box-shadow: 5px 5px 4px 5px #888888;display: table;">
    <div style="float: right; width: 100%">
      <b>{{job.JobTitle}}</b> <br />
      {{job.Organization}}. <br />
      <div style="float: right;">
        <button id="{{job.JobLabel | prepend: 'jp-bn'}}" class="btn buttonSI"
          onclick="showFun('{{job.JobLabel | prepend: "jp" }}','{{job.JobLabel | prepend: "jp-bn" }}')">Show
          Description</button>
      </div>
      <br />
      {% if job.ContactPerson %}
      Contact: {{job.ContactPerson}} <br />
      {% endif %}
      {% if job.ContactEmail %}
      Contact Email: {{job.ContactEmail}}
      {% endif %}
      <br/>
      <div id="{{job.JobLabel | prepend: 'jp'}}" style="display: none">
        <br><b> Description</b>: {{job.JobDescription}}
        {% if job.MinQual != "" %}
            <br><br><b> Minimum Qualifications</b>: {{job.MinQual}}
        {% endif %}
        {% if job.PrefQual != "" %}
            <br><br><b> Preferred Qualifications</b>: {{job.PrefQual}}
        {% endif %}
        {% if job.OrganizationInfo != "" %}
            <br><br><b> Organization Information</b>: {{job.OrganizationInfo}}
        {% endif %}
        {% if job.Salary != "" %}
            <br><br><b> Salary Information</b>: {{job.Salary}}
        {% endif %}
        {% if job.ApplicationInstructions != "" %}
            <br><br><b> Instructions for Applying</b>: {{job.ApplicationInstructions}}
        {% endif %}
        {% if job.Deadline != "" %}
            <br><br><b> Deadline</b>: {{job.Deadline}}
        {% endif %}
      </div>
    </div>
</div>

{% endfor %}

