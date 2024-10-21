---
hide:
  - navigation
  - toc
---

<style>
  .main-container {
    display: flex;
    flex-direction: column;
    gap: 15px;
    margin: 20px 50px 0px 50px;
  }

  .parent-container {
    display: grid;
    flex-wrap: wrap;
    gap: 15px;
  }

  #heading {
    grid-template-columns: 1fr 1fr;
  }

  #body {
    grid-template-columns: 1fr 1fr 1fr 1fr;
    justify-items: center;
  }

  .child-container {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: space-between;
    font-size: 15px;
  }

  .card {
    position: relative;
    border-radius: 25px;
    background-color: rgba(150,100,255,0.33);
    height: fit-content;
    width: fit-content;
    text-align: center;
    align-content: center;
    box-sizing: border-box;
  }

  .card:hover {
    background-color: rgba(200,150,255,0.45);
    transition: background-color 0.5s;
  }

  .card:active {
    background-color: rgba(100,50,200,0.22);
    transition: background-color 0.1s;
  }

  #workshop {
    height: 15vw;
    width: 20vw;
    overflow: hidden;
  }

  #workshop > img {
    position: relative;
    width: 300px;
  }

  #title {
    max-width: 50vw;
    min-width: 50vw;
    padding: 10px;
  }

  #mission, #vision {
    max-width: 30vw;
    min-width: fit-content;
    min-height: 49%;
    padding: 10px;
  }


  /* Media Queries */
  
  /* Mobile Devices */
  @media (max-width: 600px) {
    .main-container {
      margin: 10px 20px 0 20px;
    }
    
    #heading {
      grid-template-columns: 1fr;
      justify-items: center;
    }
    
    #body {
      grid-template-columns: 1fr;
    }

    #title, #mission, #vision {
      max-width: 70vw;
      min-width: 70vw;
    }

    .child-container {
      flex-direction: row;
      justify-content: center;
      gap: 20px;
    }

    #workshop {
      height: 40vw;
      width: 60vw;
    }
  }

  /* Medium Screen */
  @media (min-width: 600px) and (max-width: 900px) {
    .main-container {
      margin: 10px 20px 0 20px;
    }
    
    #heading {
      grid-template-columns: 1fr;
      justify-items: center;
    }
    
    #body {
      grid-template-columns: 1fr 1fr;
    }

    #title, #mission, #vision {
      max-width: 70vw;
      min-width: 70vw;
    }

    .child-container {
      flex-direction: row;
      justify-content: center;
      gap: 20px;
    }

    #workshop {
      height: 25vw;
      width: 35vw;
    }
  }

  /* Tablet Devices */
  @media (min-width: 900px) and (max-width: 1300px) {
    .main-container {
      margin: 15px 30px 0 30px;
    }

    #body {
      grid-template-columns: 1fr 1fr 1fr;
    }

    #workshop {
      height: 15vw;
      width: 25vw;
    }
    
    .child-container {
      flex-direction: row;
      justify-content: center;
      gap: 10px;
    }
  }
</style>

<div class='main-container'>
<h1>Welcome to AWS Knowledge Base!</h1>
  <div class='parent-container' id='heading'>
    <div class='card' id='title'>
        <img src='assets/logo/alc_logo.png' width='250'>
        <br><br>
        <h1><b>AWS Learning Club - UP Mindanao</b></h1>
        <p>Amazon Web Services Learning Club - University of the Philippines Mindanao is the <b>first official AWS student organization in Mindanao</b>. Founded in early 2024, this club fosters AWS knowledge growth through <b>workshops, knowledge sharing, and community building</b>.</p>
    </div>
    <div class='child-container'>
      <div class='card' id='mission'>
          <h1><b>Mission</b></h1>
          <p>Foster a <b>collaborative learning environment</b> to empower individuals of all backgrounds to gain proficiency in Amazon Web Services (AWS) through workshops, knowledge sharing, and community building.</p>
      </div>
      <div class='card' id='vision'>
          <h1><b>Vision</b></h1>
          <p>To become a <b>premier learning hub</b> that cultivates a skilled and passionate cloud computing community leveraging AWS to <b>drive innovation and create positive impact</b>.</p>
      </div>
    </div>
  </div>

  <h1>Explore our Workshops</h1>
  <!--Temporary ra ng links sa pics hahaha-->
  <div class='parent-container' id='body'>
    <div class='card' id='workshop'>
      <img src="https://scontent.fdvo5-1.fna.fbcdn.net/v/t39.30808-6/457263170_122149294586252999_4148721853945273900_n.jpg?_nc_cat=105&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeH9Wp6NK7PHdeHERmhkvyRMPcSPVg4TCUA9xI9WDhMJQDp4LSO58TgTIGclUJpyTSUxupz-XSkPtPgLleLMc9Q-&_nc_ohc=-6ONAV5WlmsQ7kNvgHItTZv&_nc_zt=23&_nc_ht=scontent.fdvo5-1.fna&_nc_gid=AtPkkmqeaO5xDq6woLxCWy8&oh=00_AYDbpqDcqERRudVAb3k_3yVUtqikjquLqW_SExlCrUjC6A&oe=671C88EE" alt="Workshop 1">
    </div>
    <div class='card' id='workshop'>
      <img src="https://scontent.fdvo5-1.fna.fbcdn.net/v/t39.30808-6/463323861_122159203502252999_2311708440502643717_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeHUzFPkUipbawAxQa6tVCwu2SPAKbyz887ZI8ApvLPzzkOwLqAaAlcZdV680-vwwZnwCMXO_5lY4vNUZgG71fZz&_nc_ohc=IcgvZY-AKwwQ7kNvgG_8WCa&_nc_zt=23&_nc_ht=scontent.fdvo5-1.fna&_nc_gid=AAn0lSauYAB3CxlyCghPG3h&oh=00_AYDhhwVgDhitUZqXB9PF2Q-VV7fI0_iEMjNAs2SeYHY8DA&oe=671C952A" alt="Workshop 1">
    </div>
    <div class='card' id='workshop'>
      <h2>Coming Soon</h2>
    </div>
    <div class='card' id='workshop'>
      <h2>Coming Soon</h2>
    </div>
    <div class='card' id='workshop'>
      <h2>Coming Soon</h2>
    </div>
    <div class='card' id='workshop'>
      <h2>Coming Soon</h2>
    </div>
    <div class='card' id='workshop'>
      <h2>Coming Soon</h2>
    </div>
  </div>
</div>
