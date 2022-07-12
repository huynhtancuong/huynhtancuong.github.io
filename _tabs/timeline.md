---
title: Timeline
icon: fas fa-info-circle
order: 5
layout: page
toc: true
timelines: {
  name: 'My Timeline',
  description: My timeline description,
  milestones: {
      1: {
            name: 2021 to present,
            events: {
                1: {
                  name: something1,
                  description: description of something,
                  icon: fa fa-archive,
                  link: "../about/#3-automatic-hand-washing-machine"
                },

                2: {
                  name: something2,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                },
              
                3: {
                  name: something3,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                },

                4: {
                  name: something34,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                }
          }
      },
      2: {
            name: 2020,
            events: {
                1: {
                  name: something4,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                },

                2: {
                  name: something5,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                },
              
                3: {
                  name: something6,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                }
          }
      },
      3: {
            name: 2019,
            events: {
                1: {
                  name: something7,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                },

                2: {
                  name: something8,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                },
              
                3: {
                  name: something9,
                  description: description of something,
                  icon: fa fa-address-card,
                  link: "#"
                }
          }
      }
  }
}
---


{% assign timeline = page.timelines %}
{% include timeline.html %}
