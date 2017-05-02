---
title: "Upload File"
bg: black
color: white
fa-icon: cloud-upload
---

<div class="container">
  <div class="row">
    <div class="col-md-6">
      <form action="https://getsimpleform.com/messages?form_api_token=f21c9f6d668564eb6d853a65cf8c1e77" method="post" class="form-horizontal" id="file-submit">
        <!-- the redirect_to is optional, the form will redirect to the referrer on submission -->
        <input type='hidden' name='redirect_to' value='https://www.dropbox.com/request/7lG33UjGl1Vb4fWtSqE9'/> 
          <div class="row">
            <div class="form-group form-group-lg">
              <label for="FullName" class="col-sm-3 control-label">
              <span class="cus-font">Full Name</span></label>
                <div class="col-sm-9">
                  <input type="text" class="form-control" id="FullName" name="FullName:"  data-validation="length custom" data-validation-length="min4" data-validation-regexp="^([A-Za-z ]+)$">
                  <span class="help-text">Your full name
                  </span>
                </div>
            </div>
          </div>

    <div class="row remove-margin">
       <div class="form-group form-group-lg">
        <label for="MobileNo" class="col-sm-3 control-label"> Mobile No</label>
        <div class="col-sm-9">
          <input type="text" class="form-control" id="MobileNo" name="Mobile:" data-validation="length custom" data-validation-length="min6" data-validation-regexp="^([0-9 \-+()]+)$">
          <span class="help-text">Your valid mobile number</span>
        </div>
      </div>
    </div>

    <div class="row">
       <div class="form-group form-group-lg">
        <label for="Email" class="col-sm-3 control-label"> Email</label>
        <div class="col-sm-9">
          <input type="email" class="form-control" id="MobileNo" name="Email:"  data-validation="email" >
          <span class="help-text">Your email address. e.g. mauri3dprint@gmail.com</span>
        </div>
      </div>
    </div>

    <div class="row">
       <div class="form-group">
        <div class="col-sm-offset-3 col-sm-9">
          <button type="submit" class="btn btn-lg btn-log"  id="proceed">Proceed</button>
        </div>
      </div>
    </div>
    <div class="row">
      <ul class="info-display">
        <li>Step 1: Fill up the form and click proceed.</li>
        <li>Step 2: Upload dialogue box will open.</li>
        <li> Step 3: Click Next. Dropbox file sharing service will open.</li>
        <li>Step 3: Upload File in our Dropbox. We accept only <strong>.STL</strong> and <strong>.OBJ</strong> file format.</li>
        <li>Step 4: You'll be contacted shortly with model details and pricing.</li>
      </ul>
    </div>
  </form>
  </div>

  <div class="col-md-6 hidden-xs">
    <div class="help-holder pos-main-help"> 
      <table>
          <tr>
            <th>
             <div class="help-question">
              <i class="fa fa-question"></i>
              </div>
            </th>
            <td><p class="pos-main-text">Instruction<br>
                Direct Contact</p>
            </td>
          </tr>
          <tr>
              <td>
                <p class="need-help">Need Help?</p>
              </td>          
          </tr>
      </table>
    </div> 
  </div>

  <!-- Repeat of above code except modification of css of help section to fit for smaller screen -->

  <div class="col-md-6 visible-xs">
    <div class="help-holder pos-main-help-small "> 
      <table>
          <tr>
            <th>
             <div class="help-question-small">
              <i class="fa fa-question"></i>
              </div>
            </th>
            <td><p class="pos-main-text-small">Instruction<br>
                Direct Contact</p>
            </td>
          </tr>
          <tr>
              <td>
                <p class="need-help-small">Need Help?</p>
              </td>          
          </tr>
      </table>
    </div> 
  </div>
</div>

<!-- Bootstrap model to proceed for file upload -->
{% include msgmodal.html 
        id="'proceed-modal'" 
        targetid="'#upload-modal'"  
        modalid="'upload-modal'" 
        msg="Thank you, we've received your details please click next to upload file. You'll be redirect to dropbox for upload. We'll contact you shortly once the file has been analyzed by us." 
        next-modal="'uploadnext'"%}

<script>
  $.validate({
    form : "#file-submit",
    onSuccess : function($form) {
    if ($modal_status) {
       $modal_status=false;
       return true;
       //stop form from submit
      } else {
        $('#proceed-modal').trigger('click');
        return false;
     } 
   }
  });

  $( function () {
    $modal_status=false;
    $('#uploadnext').click( function () {
      $modal_status = true;
      $('.close').trigger('click');
      $('#proceed').trigger('click')
    });
  });
</script>



