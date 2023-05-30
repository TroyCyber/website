---
layout: landingpage
title: Cyber Camps
subtitle: Cyber Camps
show_date: true
show_sidetoc: true
---
<div class="container">
    <div class="row">
    {% for camp_dict in site.data.camps %}
    {% assign camp = camp_dict[1].camp %}
    {% assign url = camp.title | downcase | replace: ' ', '-' %}
        <div class="col-md-6">
            <a href="#{{ url }}">
                <div class="text-left my-4 py-5 px-3 rounded-lg chulapa-overlay-img text-white" style="background-color: var(--primary)">
                <h2 class="py-3">{{ camp.title }}</h2>
                <p class="lead font-weight-light py-2">{{ camp.grades }}</p>
                <p class="lead font-weight-light py-2">
                    {% for session in camp.sessions %}
                        {{ session.duration | split: "," | first }}{% unless forloop.last %}, {% endunless %}
                    {% endfor %}
                </p>
                </div>
            </a>
        </div>
    {% endfor %}
    </div>
</div>

{% for camp_dict in site.data.camps %}
{% assign camp = camp_dict[1].camp %}
{% assign url = camp.title | downcase | replace: ' ', '-' %}
<div class="container mb-4">
    <h2 id="{{ url }}">
        {{ camp.title }}
    </h2>
    <p>
        <b>Description:</b>
        {{ camp.description }}
    </p>
    <p>
        <b>Grades:</b>
        {{ camp.grades }}
    </p>
    <p>
        <b>Prerequisite Experience:</b>
        {% if camp.experience.required %}
            Required experience: {{ camp.experience.description }}
        {% else %}
            No experience required: {{ camp.experience.description }}
        {% endif %}
    </p>
    <p>
        <b>Sessions:</b>
        <ul>
        {% for session in camp.sessions -%}
            <li>
                {{ session.duration }} - <span {% if session.spots > 0 %}class="available">{{ session.spots }} spots remaining{% elsif session.spots == 0 %} class="waitlist">No spots remaining{% else %} class="waitlist">{{ session.spots | times: -1 }} spots on WAITLIST{% endif %}</span>
            </li>
        {% endfor -%}
        </ul>
    </p>
    <p>
        <b>Camp Fee:</b>
        {{ camp.fee }}
    </p>
    <p>
        <b>Objectives:</b>
        <ul>
        {% for objective in camp.objectives -%}
            <li>
                <b>{{ objective.title }}</b> - {{ objective.description }}
            </li>
        {% endfor -%}
        </ul>
    </p>
    <p>
        <a class="btn btn-info text-white" href="{{ camp.registration }}" target="_blank" rel="noopener noreferrer">Register</a>
    </p>
    
</div>
{% endfor %}