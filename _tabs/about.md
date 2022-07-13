---
title: About
icon: fas fa-info-circle
order: 4
layout: post-without-title
toc: true
permalink: /about/

project-timelines: {
  name: 'Personal Projects Timeline',
  description: 'A brief stories of my 4 years journey',
  milestones: {
      4: {
            name: 2022,
            events: {
                1: {
                  name: Custom PCB of CAN Node,
                  description: "A custom CAN Node which have a STM32F103 and built-in CAN Transceiver.",
                  icon: bi bi-cpu,
                  link: "../posts/olimp-can-module/",
                  status: "done"
                },

                2: {
                  name: Differential Automobile,
                  description: "A differential drive which can avoid obstacle by using <i>tangential escape</i>.",
                  icon: fa fa-car,
                  link: "#",
                  status: "done"
                },
              
                3: {
                  name: 3-Axis Robotic Arm,
                  description: "A 3-axis robotic arm which can autonomous move to given point in space.",
                  icon: bi bi-wrench,
                  link: "#",
                  status: "done"
                },

                4: {
                  name: 6-Axis Robotic Arm,
                  description: "A 6-axis robotic arm which can autonomous move to given point and given direction of the gripper in space.",
                  icon: bi bi-wrench,
                  link: "#",
                  status: "active"
                },

                5: {
                  name: Mathematic model of DC motor,
                  description: "A mathematic model of DC motor which describe the characteristic of the motor.",
                  icon: bi bi-book,
                  link: "#",
                  status: "inactive"
                },

                6: {
                  name: Self Balancing Robot,
                  description: "A mathematical approach to build a self balancing robot",
                  icon: fa fa-car,
                  link: "#",
                  status: "inactive"
                }
          }
      },
      3: {
            name: 2021,
            events: {
                1: {
                  name: Custom PCB of LED Clock,
                  description: "A custom LED Clock based on STM32F103 and ESP8266.",
                  icon: fa fa-clock,
                  link: "#",
                  status: "done"
                },

                2: {
                  name: Custom PCB of Arduino Nano,
                  description: "A custom Arduino Nano for PCB designing practice.",
                  icon: fa fa-clock,
                  link: "#",
                  status: "done"
                }
          }
      },
      2: {
            name: 2020,
            events: {
                
                2: {
                    name: Automatic Hand Washer,
                    description: "An automatic antiseptic liquid dispenser and user's temperature monitoring.",
                    icon: fa fa-thermometer-empty,
                    link: "../posts/automatic-hand-washing-machine/",
                    status: "done"
                    },
              
                3: {
                    name: Virtual Assistance for Visually Impaired people,
                    description: "A virtual assistance for visually impaired people which based on Raspberry Pi, Google Cloud Platform.",
                    icon: fa fa-blind,
                    link: "../posts/virtual-assistance/",
                    status: "done"
                    },
              
                4: {
                    name: Self Balancing Robot,
                    description: "A practical approach to build a self balancing robot.",
                    icon: fa fa-car,
                    link: "../posts/balancing-robot-saigontech/",
                    status: "done"
                    }, 

                1: {
                    name: Make my own Speaker,
                    description: "A build of bluetooth speaker from recycled material.",
                    icon: fa fa-volume-up,
                    link: "#",
                    status: "done"
                },

                5: {
                    name: Spider bot,
                    description: "Moveable but not the mathematic approach to build it.",
                    icon: bi bi-robot,
                    link: "#",
                    status: "done"
                }
          }
      },
      1: {
            name: 2019,
            events: {
                1: {
                  name: Automatic Watering System,
                  description: "An automatic watering system for plants, which can be controlled and data monitoring on smartphone.",
                  icon: fa fa-tint,
                  link: "#",
                  status: "done"
                },

                2: {
                  name: Wireless Room Light  ,
                  description: "A wireless room light control which based on ESP8266 microcontroller.",
                  icon: fa fa-lightbulb,
                  link: "#",
                  status: "done"
                },
              
                3: {
                  name: Line Follower Robot,
                  description: "A line follower robot which based on GaraStem educational kit.",
                  icon: fa fa-car,
                  link: "#",
                  status: "done"
                },

                4: {
                  name: LED Board Decoration,
                  description: "A LED board for camping in Datlat, for decoration and competition between classes.",
                  icon: fa fa-lightbulb,
                  link: "#",
                  status: "done"
                }
          }
      }
  }
}

---

> This page is still in process of building.
{: .prompt-danger}

Hi :wave:, my name is **Huynh Tan Cuong**, and people in Russia call me by the name **Хюинь Тан Куонг**.

As of July 2022, I'm a first-year Bachelor student at *ITMO University* studying *Mechatronic and Robotics*. Before that, I was a high school student at *Ly Thuong Kiet High school*.

My primary interests are in making robot, DIY things and study the magic of math which stand behind the whole robot industry. 

---

# Personal Projects

{% assign timeline = page.project-timelines %}
{% include timeline.html %}
---

# Competitions

---

# Work experience
* R&D at OhStem
* Member at OLIMP Club[^OLIMP]

---

# Education
* Learn Mechatronic and Robotics at ITMO University (2021 - Present)
* DEVIOT training center:
    - PCB Designing
    - Basic C Programming
    - Embedded Linux Programming
    - STM32
* Udemy:
    - Robot Operating System (ROS)
    - Gazebo simulator

---

# Skills

## Language skills
* Vietnamese
* Russian
* English

## Computer skills
* Microsoft Office
* C/C++
* Matlab
* Python
* Java
* PostgreSQL 

## Interpersonal / Life skills
* Analytical Skills
* Detail-oriented
* Team leader
* Multi-tasking

---
# Reverse Footnote
[^OLIMP]: The OLIMP Association (Open Laboratory of Ideas, Methods and Practices) is an association of open laboratories designed to develop ideas for the exchange of experience, self-development and project activities.