# Jornaya_Integration
Jornaya_Integration

# Step 1: Add Hidden Fields inside thje form tag


              <input type="hidden" id="leadid_token" name="universal_leadid" value="">
              <input type="hidden" id="xxTrustedFormCertUrl" name="xxTrustedFormCertUrl" value="">
              <input type="hidden" id="xxTrustedFormPingUrl" name="xxTrustedFormPingUrl" value="">
              <input type="hidden" id="ip_address" name="ip_address" value="">
              <input type="hidden" id="user_agent" name="user_agent" value="">
              <input type="hidden" id="landing_page_url" name="landing_page_url" value="">

              
This Screenshot will help that.. 

<img width="850" height="228" alt="{92682629-5362-4CAB-B1D9-651599F41362}" src="https://github.com/user-attachments/assets/a083d2fa-c582-42b0-978b-78f50e257f59" />

# Step 2: Add these scripts exactly below the form tag.

 Jornaya LeadID Script -->
      <script id="LeadiDscript" type="text/javascript">
      (function() {
      var s = document.createElement('script');
      s.id = 'LeadiDscript_campaign';
      s.type = 'text/javascript';
      s.async = true;
      s.src = '//create.lidstatic.com/campaign/9d8cf604-55f2-d087-7177-7e9ecff6a0da.js?snippet_version=2';
      var LeadiDscript = document.getElementById('LeadiDscript');
      LeadiDscript.parentNode.insertBefore(s, LeadiDscript);
      })();
      </script>
      <noscript><img src='//create.leadid.com/noscript.gif?lac=A7AE383F-5A16-755E-F87B-F9FAB6D10A94&amp;lck=9d8cf604-55f2-d087-7177-7e9ecff6a0da&amp;snippet_version=2' alt="" width="1" height="1" /></noscript>

 ActiveProspect TrustedForm Script -->
      <script type="text/javascript">
      (function() {
          var tf = document.createElement('script');
          tf.type = 'text/javascript'; tf.async = true;
          tf.src = ("https:" == document.location.protocol ? "https" : "http") + "://api.trustedform.com/trustedform.js?field=xxTrustedFormCertUrl&ping_field=xxTrustedFormPingUrl&l=" + new Date().getTime() + Math.random();
          var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(tf, s);
      })();
      </script>
      <noscript>
          <img src="https://api.trustedform.com/ns.gif" alt="" width="1" height="1" />
      </noscript>

    const ipField = document.getElementById("ip_address");
 
   Fetch public IP as soon as the page loads
        fetch("https://ipinfo.io/json")
            .then(response => {
                if (!response.ok) throw new Error('Response not OK');
                return response.json();
            })
            .then(data => {
                if (ipField) ipField.value = data.ip || "";
            })
            .catch(error => {
                console.warn("Primary IP fetch failed, trying fallback:", error);
                fetch("https://api.ipify.org?format=json")
                    .then(res => res.json())
                    .then(data => {
                        if (ipField) ipField.value = data.ip || "";
                    })
                    .catch(err => console.error("Fallback IP fetch also failed:", err));
            });     



      

