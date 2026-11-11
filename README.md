# Jornaya_Integration
Jornaya_Integration

# Step 1: Add Hidden Fields inside the form tag


              <input type="hidden" id="leadid_token" name="universal_leadid" value="">
              <input type="hidden" id="xxTrustedFormCertUrl" name="xxTrustedFormCertUrl" value="">
              <input type="hidden" id="xxTrustedFormPingUrl" name="xxTrustedFormPingUrl" value="">
              <input type="hidden" id="ip_address" name="ip_address" value="">
              <input type="hidden" id="user_agent" name="user_agent" value="">
              <input type="hidden" id="landing_page_url" name="landing_page_url" value="">

              
This Screenshot will help that.. 

<img width="850" height="228" alt="{92682629-5362-4CAB-B1D9-651599F41362}" src="https://github.com/user-attachments/assets/a083d2fa-c582-42b0-978b-78f50e257f59" />

# Step 2: Add these scripts exactly below the form tag.

    
    <script id="LeadiDscript" type="text/javascript">
    (function() {
    var s = document.createElement('script');
    s.id = 'LeadiDscript_campaign';
    s.type = 'text/javascript';
    s.async = true;
    s.src = '//create.lidstatic.com/campaign/b5f60acf-5e98-9523-4c17-d6cb9aa2a803.js?snippet_version=2';
    var LeadiDscript = document.getElementById('LeadiDscript');
    LeadiDscript.parentNode.insertBefore(s, LeadiDscript);
    })();
    </script>
    <noscript><img src='//create.leadid.com/noscript.gif?lac=A7AE383F-5A16-755E-F87B-F9FAB6D10A94&lck=b5f60acf-5e98-9523-4c17-d6cb9aa2a803&snippet_version=2' /></noscript>
     

   <!-- TrustedForm -->
    <script type="text/javascript">
    (function() {
    var tf = document.createElement('script');
    tf.type = 'text/javascript';
    tf.async = true;
    tf.src = ("https:" == document.location.protocol ? 'https' : 'http') +
      '://api.trustedform.com/trustedform.js?field=xxTrustedFormCertUrl&use_tagged_consent=true&l=' +
      new Date().getTime() + Math.random();
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(tf, s);
    })();
    </script>
    <noscript>
    <img src='https://api.trustedform.com/ns.gif' />
    </noscript>
<!-- End TrustedForm -->

   
 
       const ipField = document.getElementById("ip_address");
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




and , Please make sure. your TCPA text as shown in below screenshot must have this ID tag: leadid_tcpa_disclosure

<img width="687" height="192" alt="{E618FCB4-B2BA-4DA2-A4ED-DF338F547274}" src="https://github.com/user-attachments/assets/2bfdf7ba-5e68-4231-84a8-5c70e273932b" />

and I am also dropping code example below. 

      <input type="checkbox" id="leadid_tcpa_disclosure" class="form-check-input" /> 
... 
# Step 3: Form fields ID Integrations. 
I want you to make sure. Ever form fields must have unique form ID. So, Our bot system can work, If any of it is missing, The system will not work. For code expample, I want you to look at this lnading page

https://mvaquotes.us/ 

      

