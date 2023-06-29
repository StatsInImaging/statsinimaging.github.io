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

Interested in posting a job? Click here to fill out the submission form.

{% for job in site.data.job_postings %}

<div class="jp"
  style="border: 1px solid black; margin: 20px; width: 100%; padding: 10px; box-shadow: 5px 5px 4px 5px #888888;display: table;">
    <div style="float: right; width: 100%">
      <b>{{job.JobTitle}}</b> <br />
      {{job.Institution}}. <br />
      <div style="float: right;">
        <button id="{{job.id | prepend: 'jp-bn'}}" class="btn btn-ps"
          onclick="showFun('{{job.id | prepend: "jp" }}','{{job.id | prepend: "jp-bn" }}')">Show
          Description</button>
      </div>
      <br />
      {% if job.ContactName %}
      Contact: {{job.ContactName}} <br />
      {% endif %}
      {% if job.ContactEmail %}
      Contact Email: {{job.ContactEmail}}
      {% endif %}
      <br/>
      <div id="{{job.id | prepend: 'jp'}}" style="display: none">
        <b> Description</b>: {{job.Description}}
      </div>
    </div>
</div>

{% endfor %}

