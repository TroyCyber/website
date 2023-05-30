---
layout: splashpage
title: History of Troy Cyber
---
<main class="container-lg  pb-3 chulapa-landingpage-color chulapa-bg-landingpage">
    <div class="container">
        <div class="row">
            <div class="col-md-12">
                <div class="main-timeline">
                    {% for year in site.data.history.years %}
                    <div class="timeline">
                        <a id="{{ year.year }}" href="#{{ year.year }}" class="timeline-content">
                            <div class="timeline-icon"><i class="fa fa-globe"></i></div>
                            <div class="timeline-year">{{ year.year }}</div>
                            <h3 class="title">{{ year.events[0].name }}</h3>
                            <p class="description">
                                {% for event in year.events %}
                                <b>{{ event.name }}</b>
                                <br>
                                {{ event.description }}
                                <br>
                                {{ event.date | date: "%B %d, %Y" }}
                                <br>
                                <br>
                                {% endfor %}
                            </p>
                        </a>
                    </div>
                    {% endfor %}
                </div>
            </div>
        </div>
    </div>
</main>