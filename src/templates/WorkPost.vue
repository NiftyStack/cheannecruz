<template>
  <Layout>
    <section class="work-page__main-banner">
      <g-image
        :src='$page.post.mainBannerImage'
        :alt='$page.post.title'
        fit="contain"
        class="work-page__main-banner-img"
        immediate="true"
      />
    </section>
    <section class="work-page__section">
      <div class="work-page__main-content">
        <h1 class="work-page__heading">{{$page.post.title}}</h1>
        <small class="work-page__name">{{$page.post.projectName}}</small>
        <p class="work-page__role">
          <span v-for="role in $page.post.roles" class="work-page__role-item">
            {{role}}
          </span>
        </p>
        <div class="work-page__content" v-html="noFirstLetter($page.post.content)"></div>
      </div>
    </section>
  </Layout>
</template>


<page-query>
  query Work ($path: String){
    post: workPost (path: $path) {
      title
      roles
      content
      mainBannerImage
      dateCreated
      projectName
      projectURL
    }
  }
</page-query>
<script>
  export default {
    data() {
      return {
        firstLetter: '',
      }
    },
    methods: {
      formatDate(thisDate) {
        const months = ["JAN", "FEB", "MAR","APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"];
        let current_datetime = new Date(thisDate);
        let formatted_date = current_datetime.getDate() + " " + months[current_datetime.getMonth()] + " " + current_datetime.getFullYear();
        return formatted_date;
      },
      noFirstLetter(content) {
        const strip = content.substring(4);
        const pTag = content.slice(0, 3) + '<span>' + content.slice(3, 4) + '</span>';
        return pTag + strip;
      }
    }
  };
</script>
<style lang="scss">
.work-page__main-banner {
  position: relative;
  height: 50vh;
  overflow: hidden;
}
.work-page__main-banner-img {
  width: 100%;
  height: 100%;
  display: block;
  object-fit: cover;
}
.work-page__section {
  background: #fff;
  overflow: hidden;
  padding: 0 30px;

  .work-page__main-content {
    max-width: 980px;
    margin: 0 auto;

    img {
      width: 100%;
    }
  }
}
.work-page__heading {
  font-family: 'Montserrat Alternates', sans-serif;
  padding: 1.5em 0 0;
  font-size: 46px;
  margin-bottom: 0;
  font-weight: 700;
}

.work-page__name {
  color: #586069;
  font-size: 14px;
  line-height: 2;
  display: block;
  text-transform: uppercase;
  padding-bottom: 1em;
}

.work-page__role {
  color: #586069;
  font-size: 14px;
  padding-bottom: 3em;
}

.work-page__role-item {
  border: 1px solid #01a2c4;
  padding: 5px 15px;
  border-radius: 20px;
  color: #01a2c4;
  margin: 5px;
  display: inline-block;
}

.work-page__content {
  line-height: 2;
  margin-bottom: 5em;

  span:first-of-type {
    float: left;
    font-size: 100px;
    margin-right: 10px;
    vertical-align: baseline;
    font-weight: 700;
    height: 100px;
    line-height: 1;
    margin-top: -5px;
  }

  .main-img-holder {
    img {
      float: left;
      margin: 0 20px 10px 0px;
      max-width: 400px;
    }

    @media only screen and (max-width: 667px) {

      p {
        text-align: center;
      }

      img {
        float: none;
        margin: 0 auto;
      }
    }
  }

  .img-holder {
    margin: 0 auto;
    display: block;
    max-width: 600px;

    p, p.desc {
      text-align: center;
      margin: 0;
      color: #586069;
      font-size: 12px;
    }
    img {
      margin: 0px;
      max-width: 600px;
    }
  }

  .img-holder--full-size {
    max-width: 100%;
    width: 100%;

    img {
      margin: 0px;
      max-width: 100%;
      width: 100%;
    }
  }

  .nifty-logo {
    min-width: 300px;

    img {
      margin: 20px 120px;
      max-width: 80px;
    }
  }

  .kraite-logo {
    min-width: 300px;

    img {
      margin: 30px 120px;
      max-width: 200px;
    }
  }

  p {
    margin: 2em 0;
    text-align: justify;
  }

  strong {
    font-weight: 700;
  }

  .references {
    color: #586069;
    font-size: 12px;
  }

  ul {
    display: inline-block;
    margin: 0;
    list-style: none;
  }

  ul li::before {
    content: "\2022";
    color: #2BB4F7;
    font-weight: bold;
    display: inline-block;
    width: 1em;
    margin-left: -1em;
  }
}

.ending-note {
  width: 100%;
  text-align: center;
  color: #01a2c4;
}

.work-page__button-link {
  display: block;
  padding: 0px 70px 0px 20px;
  align-self: flex-end;
  color: #fff;
  text-decoration: none;
  font-weight: 700;
  font-size: 14px;
  position: relative;
  line-height: 55px;
  transition: all 0.5s ease;
  -webkit-transition: all .5s ease;
  border: 2px solid #f85ccf;
  background: #f85ccf;
  min-width: 150px;
  max-width: 150px;
  border-radius: 3px;
  margin: 0 auto;

  &::before {
    content: '';
    position: absolute;
    width: 8px;
    height: 8px;
    right: 30px;
    bottom: 42%;
    -webkit-transform: translateY(-50%);
    transform: translateY(-50%);
    z-index: 20;
    border-left: 2px solid #fff;
    border-bottom: 2px solid #fff;
    -webkit-transform: rotate(-135deg);
    transform: rotate(-135deg);
    box-sizing: border-box;
    transition: all 0.5s ease;
    -webkit-transition: all .5s ease;
  }

  &::after {
    content: '';
    position: absolute;
    width: 30px;
    height: 30px;
    z-index: 20;
    right: 18px;
    bottom: 12px;
    border: 2px solid #fff;
    box-sizing: border-box;
    border-radius: 50px;
    transition: all 0.5s ease;
    -webkit-transition: all .5s ease;
  }

  &:hover {
    border: 2px solid #c648b1;
    background: #c648b1;
  }

  &:disabled {
    opacity: 0.5;
  }
}
</style>