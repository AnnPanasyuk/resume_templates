<template>
<div class="resume">
  <div class="leftCol m_box">
    <div class="shadow"></div>
    <div class="heading" id="myselfpic">
    </div>

    <div class="left-info">
      <div class="contact">
        <div class="section-headline contact-headline">
          {{ lang.contact }}
        </div>
        <div v-if="person.birth" class="item">
          <div class="icon">
            <i class="material-icons">account_circle</i>
          </div>
          <div class="text">
            <ul>
              <li> {{ lang.born }} {{person.birth.year}} </li>
            </ul>
          </div>
        </div>

        <div class="item">
          <div class="icon">
            <i class="material-icons">location_city</i>
          </div>
          <div class="text">
            <ul>
              <li>{{person.contact.street}}</li>
              <li>{{person.contact.city}}</li>
            </ul>
          </div>
        </div>

        <a :href="contactLinks.phone">
          <div class="item">
            <div class="icon">
              <i class="material-icons">phone</i>
            </div>
            <div class="text">
              {{person.contact.phone}}
            </div>
          </div>
        </a>

        <a :href="contactLinks.email">
          <div class="item">
            <div class="icon">
              <i class="material-icons">email</i>
            </div>
            <div class="text">
              {{person.contact.email}}
            </div>
          </div>
        </a>

        <a v-if="person.contact.github" :href="contactLinks.github" target="_blank">
          <div class="item">
            <div class="icon">
              <i class="fa fa-github"></i>
            </div>
            <div class="text">
              <span>github.com/{{person.contact.github}}</span>
            </div>
          </div>
        </a>

        <a v-if="person.contact.linkedin" :href="contactLinks.linkedin" target="_blank">
          <div class="item">
            <div class="icon">
              <i class="fa fa-linkedin"></i>
            </div>
            <div class="text">
              <span>{{person.contact.linkedin}}</span>
            </div>
          </div>
        </a>

        <a v-if="person.contact.skype" href="https://join.skype.com/invite/hKfouIKMtlAp" target="_blank">
          <div class="item">
            <div class="icon">
              <i class="fa fa-skype"></i>
            </div>
            <div class="text">
              <span>{{person.contact.skype}}</span>
            </div>
          </div>
        </a>
      </div>

      <div class="item">
        <div class="section-headline">
          {{ lang.professional_skills }}
        </div>
        <div class="skill" v-for="skill in person.skills" :key="skill.name">
          <div class="right">
            <span>- {{skill.name}}&nbsp;</span>
          </div>
        </div>
      </div>

      <div class="item">
        <div class="section-headline">
          {{ lang.skills }}
        </div>
        <div class="skill" v-for="skill in person.softSkills" :key="skill.name">
          <div class="right">
            <span>- {{skill.name}}&nbsp;</span>
          </div>
        </div>
      </div>

      <div class="item last">
        <div class="section-headline">
          Languages
        </div>
        <div class="text language" v-for="language in person.languages" :key="language.item">
          <span class="language-item">
            - {{ language.item }}
          </span>
        </div>
      </div>
    </div>
  </div>

  <div class="rightCol">
    <div class="title">
      <h2>{{person.name.first}} {{person.name.middle}} {{person.name.last}}</h2>
      <div>{{person.position}}</div>
    </div>

    <div class="section-headline">{{ lang.experience }}</div>
    <div class="block" v-for="experience in person.experience" :key="experience.company">
      <div class="block-helper"></div>
      <div class="headline caption">{{experience.position}} at {{experience.company}}</div>
      <div class="subheadline">{{experience.timeperiod}}</div>
      <ul>
        <li class="list-item-info" v-for="item in experience.description" :key="item.name">
          - {{item.name}}
        </li>
      </ul>
    </div>

    <div class="section-headline">{{ lang.education }}</div>
    <div class="block" v-for="education in person.education" :key="education.degree">
      <div class="block-helper"></div>
      <div class="headline caption">{{education.degree}}</div>
      <div class="subheadline">{{education.timeperiod}}</div>
      <p class="info">
        {{education.description}}
      </p>
    </div>

<!--    <div class="section-headline">{{ lang.professional_skills }}</div>-->
<!--    <div class="block" v-for="skill in person.skills" :key="skill.name">-->
<!--      <div class="block-helper"></div>-->
<!--      <h3 class="headline">{{skill.name}}</h3>-->
<!--    </div>-->
  </div>

  <div style="clear:both;"></div>
</div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';
const name = 'material-dark';

export default Vue.component(name, getVueOptions(name));
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.resume {
  font-family:'Roboto' !important;
  background: #DB6D4A;
}
a {
  cursor:pointer;
}
.description-personal {
  margin-left:20px;
  margin-top:20px;
  padding-right:40px;
  text-align:justify;
  font-family:Roboto;
}
.title {
  right:25px;
  padding-left:20px;
  padding-top:20px;
  bottom:25px;
  h2 {
    text-transform:uppercase;
    display:block;
    line-height: 36px;
    font-size:1.17em;
    -webkit-margin-before:1em;
    -webkit-margin-after:.5em;
    -webkit-margin-start:0;
    -webkit-margin-end:0;
    color: #160B08;
    padding-top:0;
    margin-top:0;
    margin-bottom: 0;
    letter-spacing: 7px;
    font-weight:400;
  }
  div {
    margin: 0;
    padding:0;
    line-height:15pt;
    font-weight:500;
    letter-spacing:3px;
    color: #160B08;
    display:block;
    font-size:14pt;
    -webkit-margin-before:0em;
    -webkit-margin-start:0;
    -webkit-margin-end:0;
    text-transform:uppercase;
    opacity:0.8;
  }
}
.section-headline {
  text-transform:uppercase;
  font-weight:500;
  letter-spacing:3px;
  font-size:10pt;
  opacity:0.8;
  margin-left:20px;
  margin-top: 20px;
  margin-bottom: 8px;
  color: #2C160F;
}
.c {
  clear:both;
}
li {
  margin:0;
  padding:0;
  list-style-type:none;
  padding-top:9px;
}
ul {
  margin:0;
  padding:0;
  list-style-type:none;
}
p {
  margin-top:0;
  margin-bottom:25px;
  font-family:'Roboto', sans-serif;
  font-weight:300;
  font-size:10pt;
  line-height:17pt;
}
.m_box {
  box-shadow:0 2px 5px 0 rgba(0,0,0,0.16), 0 2px 10px 0 rgba(0,0,0,0.12);
}
.fa, .material-icons {
  display:inline-block;
  font-style:normal;
  font-weight:normal;
  line-height:1;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  font-size:26px;
}
h1, h3, h5, h6 {
  font-weight:400;
  margin:0;
}
h2 {
  font-weight:400;
  font-weight:500;
  margin:0;
  margin:0;
  font-size:22pt;
  line-height:37pt;
}
h4 {
  font-weight:400;
  margin:0;
  font-size:12pt;
  line-height:20pt;
  opacity:1;
}
.rightCol {
  width:63.5%;
  height:100%;
  float:right;
  display:flex;
  flex-direction:column;
  .block {
    width: 93%;
    position:relative;
    background-color:#ffffff;
    padding:12px;
    margin-top:5px;
    margin-bottom:5px;
    display:inline-block;
    box-shadow: 0 2px 5px 0 #582C1E, 0 2px 10px 0;
    .headline {
      font-weight:300;
      display:block;
      font-size:15px;
      color: #160B08;
    }
    .headline.caption {
      font-weight:400;
    }
    .subheadline {
      color: #2C160F;
      display:block;
      font-size:14px;
      font-weight:300;
    }
    .info {
      font-size:14px;
      color: #160B08;
      margin-bottom:0;
      padding-top:20px;
    }
    .list-item-info {
      padding-top: 6px;
      font-size:14px;
      color: #160B08;
      margin-bottom:0;
      font-weight: 300;
    }
    .icon {
      width:16%;
      float:left;
      margin-left:0;
      .fa, .material-icons {
        text-align:center;
        display:block;
        font-size:30pt;
      }
    }
    .content {
      width:80%;
      position:absolute;
      height:96%;
      left:17%;
      padding-right:3%;
      text-align:left;
      display:flex;
      flex-direction:column;
      .item {
        border-bottom:1px solid #bdbdbd;
        flex:1;
        width:97%;
        display:flex;
        justify-content:center;
        flex-direction:column;
        text-align:left;
        padding-top:0;
        span {
          color:#d8ab94;
          margin-top:0;
          font-size:10pt;
          line-height:16pt;
        }
        p {
          margin-top:5px;
        }
      }
      .item:last-of-type {
        border-bottom-style:none;
        border-bottom-style:none;
      }
    }
  }
}
.leftCol {
  width:35%;
  height:100%;
  float:left;
  padding:0;
  text-align:left;
  color:rgba(255,255,255,0.59);
  overflow:hidden;
  display:block;
  .section-headline {
    color: #FDF2EF;
    margin-bottom: 6px;
    margin-top: 24px;
  }
  a {
    color:rgba(255,255,255,0.59);
    text-decoration:none;
  }
  .heading {
    background-color:white;
    background-repeat:no-repeat;
    background-size:cover;
    background-position:center;
    position:relative;
    width:100%;
    height:277px;
  }
  .left-info {
    background-color: #83412D;
    width: 100%;
    padding: 40px 0 0;
    height: 100%;
  }
  .contact {
    .item {
      display: flex;
      align-items: center;
      margin-top: 6px;
    }
  }
  .contact-headline {
    margin-top: 0;
  }
  .item {
    width:100%;
    margin-top: 4px;
    float:left;
    color: #FDF2EF;
    .fa, .material-icons {
      display:inherit;
      text-align:center;
    }
    .icon {
      width:20%;
      float:left;
    }
    .text {
      float:right;
      width:69%;
      padding-right:10%;
      padding-top:0;
      display:block;
      font-size:15px;
      font-weight:300;
      li {
        padding-top:0;
        display:block;
        font-size:15px;
        font-weight:300;
      }
    }
    span {
      font-weight:300;
    }
    .skill {
      clear:both;
      width:97%;
      padding-top:4px;
      .left {
        float:left;
        width:10%;
        padding-top:3px;
        i:nth-child(2) {
          float:left;
          padding-top:4px;
        }
      }
      .right {
        float:right;
        width:93%;
        .progress {
          float:left;
          position:relative;
          height:2px;
          display:block;
          width:95%;
          background-color:rgba(255,255,255,0.19);
          border-radius:2px;
          margin:0.5rem 0 1rem;
          overflow:visible;
          margin-bottom:10px;
          .determinate {
            background-color:#78909c;
            position:absolute;
            top:0;
            bottom:0;
            .fa, .material-icons {
              font-size:13px;
              position:absolute;
              top:-4px;
              right:-2px;
              margin-left:50%;
              color:white;
            }
          }
        }
      }
    }
  }
  .item.last .text {
    border-bottom-style:none;
    padding-bottom:0;
  }
  .item.last .language {
    float: left;
    padding-left: 7%;
    .language-item {
      display: block;
      padding-bottom: 4px;
    }
  }
}
#myselfpic {
  background-image:url('../../resume/id.jpg');
  color:black;
}
#githubIcon {
  width:25px;
  padding-left:17px;
}

</style>
