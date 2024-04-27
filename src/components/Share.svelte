<script>
    const webUrl= "https://nepalforeigntrade.netlify.app/";
    const link= {
        fbLink: `https://facebook.com/share.php?u=${webUrl}`,
        twitterLink: `https://twitter.com/share?url=${webUrl}`,
        linkedinLink: `https://linkedin.com/sharing/share-offsite/?url=${webUrl}`,
        redditLink: `https://reddit.com/submit?url=${webUrl}`,
    };
  
    const copyLink=()=> navigator.clipboard.writeText(webUrl);
  </script>
  
  <div class="share-container">
    <span>Share this page?</span>
  
    <div class="links">
      <a href={link.fbLink} target="_blank">
        <i class="fa-brands fa-square-facebook"></i>
      </a>
      <a href={link.twitterLink} target="_blank">
        <i class="fa-brands fa-square-twitter"></i>
      </a>
      <a href={link.linkedinLink} target="_blank">
          <i class="fa-brands fa-linkedin"></i>
      </a>
      <a href={link.redditLink} target="_blank">
        <i class="fa-brands fa-square-reddit"></i>
      </a>
      <i on:click={copyLink} class="fa-solid fa-copy"></i><br>
    </div>
  </div>
  
  <style>
    span{
      margin-bottom: .5rem;
      text-decoration: underline;
    }
    .share-container{
      padding: .5rem;
      width: max-content;
      border-radius: 3px;
      flex-direction: column;
    }
    i{
      margin: 0 .25rem;
      font-size: 1.55rem;
      color: #797979;
      cursor: pointer;
      transition: .2s;
    }
    i:hover{
      color: #000;
    }
  </style>