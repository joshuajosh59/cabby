<?php    //print_r($car_type);die();?>
<?php if($this->session->flashdata('Wrong_email')):?>
 <script>alert("Mobile no already Exists!!");</script>
<?php endif;?>
<?php include('header.php');?>
<script>
function validateForm() {
    var x = document.forms["myForm"]["fname"].value;
	var y = document.forms["myForm"]["lname"].value;
	var z = document.forms["myForm"]["city_id"].value;
	var a = document.forms["myForm"]["car_type_id"].value;
	var b = document.forms["myForm"]["car_model_id"].value;
	var c = document.forms["myForm"]["pass"].value;
	var d = document.forms["myForm"]["email"].value;
	var e = document.forms["myForm"]["mob"].value;
	var f = document.forms["myForm"]["carnumber"].value;
	 
    if (x == "") {
        alert("First Name must be filled out");
        return false;
    }
	 else if (y == "") {
        alert(" Last Name must be filled out");
        return false;
    }
	else if (d == "") {
        alert("Please Enter e-mail");
        return false;
    }
	else if (e == "") {
        alert("Please Enter Mobile Number");
        return false;
    }
	else if (c == "") {
        alert("Please Enter Password");
        return false;
    }
	else if (z == "") {
        alert("Please Select City");
        return false;
    }
	else if (a == "") {
        alert("Please Select Car Type");
        return false;
    }
	else if (b == "") {
        alert("Please Select Car Model");
         
        return false;
    }
	else if (f == "") {
        alert("Please Enter Car Number");
        return false;
    }
	
	

}
</script>

<script>
function getId(val){
 $.ajax({
        type: "POST",
        url: "<?php echo base_url();?>index.php/Welcome/car_model",
        data: "car_type_id="+val,
        success: 
        function(data){
        $('#car_model_id').html(data);
        }
    });
}   
</script> 


<script> 
function setId(val)
{
        $.ajax({
            type: "POST",
            url: "<?php echo base_url();?>index.php/Booking_controller/get_codecountry",
            data: "id="+val,
            success:
                function(data){
                    $('#phonecode').val(data);
                }
        });
}
	
	
</script>





<div class="main_banner pt-100 pb-100" style="background-image:url(<?php echo base_url($header_data['image_driverregister']);?>); !important;">

    <div class="container">


    <div class="col-md-7 col-sm-12 col-xs-12 inner_main_banner pt-60 hidden-xs">

    
 <?php echo $Get_driver_data['description'];?>
    
    </div>
    <div class="col-md-1 col-sm-12 col-xs-12 inner_main_banner hidden-xs"></div>
    
    <div class="col-md-4 singup_right">
        
        <div class="form_heading">
		<div class="clear"></div>
        <h2><?php echo $this->lang->line('driversignup');?></h2>
    </div>
       <form name="myForm" action="<?php echo base_url();?>index.php/Useraccounts/driver_signup" onsubmit="return validateForm()" method="post">
        <div class="col-md-6 form-group">
            <input class="form-control newsignup" id="fname" name="fname" placeholder="<?php echo $this->lang->line('firstname');?>"  type="text">
        </div>
        <div class="col-md-6 form-group">
            <input class="form-control newsignup" id="lname" name="lname" placeholder="<?php echo $this->lang->line('lastname');?>"  type="text">
        </div>
        
         <div class="col-sm-12 form-group left_icon_input">
            <i class="fa fa-envelope input_email_envelope" aria-hidden="true"></i>
            <input class="form-control newsignup" id="email" name="email" placeholder="<?php echo $this->lang->line('youremail');?>"  type="email">            
        </div>
        
          <div class="col-sm-12 form-group left_icon_input">
            <i class="" aria-hidden="true"></i>
             <select class="form-control newsignup" id="country" name="country" onchange="setId(this.value);">
             
            <?php foreach($country as $country_list){ ?>
                                    <option  value="<?php echo $country_list['id'];?>" <?php if($country_list['id'] == 156){ ?> selected <?php } ?>><?php echo $country_list['name']; ?></option>
        <?php } ?>
          </select>
        </div>
    
                    
          <div class="col-md-3 form-group">
              <input type="text" name="phonecode"  id="phonecode" value="+234" class="form-control newsignup" style="background-color: #fff; !important;" readonly="readonly">
        </div>
        <div class="col-md-9 form-group">
           <input class="form-control newsignup" id="mob" name="mob" placeholder="_____-____" type="text" maxlength="11">    
        </div>
        
         
        
        <div class="col-sm-12 form-group left_icon_input">
            <i class="fa fa-lock input_password_lock" aria-hidden="true"></i>
            <input class="form-control newsignup" id="pass" name="pass" placeholder="<?php echo $this->lang->line('yourpass');?>"  type="password">            
        </div>
       
    
      
        
        <div class="col-sm-12 form-group left_icon_input">
            <i class="" aria-hidden="true"></i>
             <select name="city_id" id="city_id"  class="form-control newsignup">
             <option value="">-------- <?php echo $this->lang->line('selectcity');?> --------</option>
             <?php foreach($city as $model){ ?>
            <option value="<?php echo $model['city_id'];?>"><?php echo $model['city_name'];?></option>         
            <?php } ?>
          </select>
        </div>
        
	
		
        <div class="col-sm-12 form-group left_icon_input">
            <i class="" aria-hidden="true"></i>
            <select name="car_type_id" id="car_type_id" onchange="getId(this.value)" class="form-control newsignup">
             <option value="">-------- <?php echo $this->lang->line('selectcar');?> --------</option>
            <?php foreach($car_type as $model){ ?>
            <option value="<?php echo $model['car_type_id'];?>"><?php echo $model['car_type_name'];?></option>         
            <?php } ?>
          </select>          
        </div>
        
       <div class="col-sm-12 form-group left_icon_input">
            <i class="" aria-hidden="true"></i>
             <select name="car_model_id" id="car_model_id" class="form-control newsignup">
        
          <option value="">-------- <?php echo $this->lang->line('selectmodel');?> --------</option>   
          
          </select>  
        </div>  
          <div class="col-sm-12 form-group left_icon_input">
            <i class="fa fa-building input_city_building" aria-hidden="true"></i>
            <input class="form-control newsignup" id="carnumber" name="carnumber" placeholder="<?php echo $this->lang->line('carnumber');?>"  type="text">            
        </div>
        
        	 <div class="col-sm-12 form-group left_icon_input">
            <i class="" aria-hidden="true"></i>
             <select name="driver_category" id="driver_category" class="form-control newsignup">
        
          <option value="">-------- <?php echo $this->lang->line('ridetype');?> --------</option>   
		      <option value="1">   <?php echo $this->lang->line('normal');?>  </option>  
	              <option value="2">   <?php echo $this->lang->line('rental');?>  </option>  
	              <option value="3">   <?php echo $this->lang->line('both');?> </option>  
          </select>    
        </div>
		
        <!--<div class="col-sm-12 form-group left_icon_input">
            <i class="fa fa-circle input_invite_circle" aria-hidden="true"></i>
            <input class="form-control newsignup" id="city" name="lname" placeholder="Invite Code (optional)" required="" type="text">            
        </div>-->
        
                <br></br>
        <span class="col-md-12 tc_pp"> 
          <center style="line-height:1.5">
	<?php 
                                                                    if($site_lang == 'english'){
																	echo 'By registering, you are agreeing to';
																     }
																   else{
																	echo 'By registering, you are agreeing to';
																    }
																	?>	 <a class="" target="blank" href="http://13.78.177.152/index.php/terms/driver"> 	<?php 
                                                                    if($site_lang == 'english'){
																	echo 'Terms & Conditions';
																     }
																   else{
																	echo 'Terms & Conditions';
																    }
																	?> <?php echo $header_data['app_name'];?></a></center> </span> 
        
        <div class="col-md-12 form-group">
            <input class="next_btn" value="<?php echo $this->lang->line('signup');?>" width="100%" type="submit">
        </div>
        
        <!--<span class="col-md-12 tc_pp">You agree to <a href="#">Apporio Terms and Conditions</a> and <a href="#">Privacy Policy</a>.</span>-->
        </form>
        <div class="col-md-12">
            <a href="<?php echo base_url();?>index.php/Welcome/driver_signin"><button class="aleardy_btn"><?php echo $this->lang->line('alreadysignin');?></button></a>
        </div>
        <div class="clear"> </div>

    </div>
    

</div>
  
</div>
 
</div>
<script type="text/javascript" src="<?php echo base_url();?>/js/jquery-1.11.3.min.js"></script> 
<script type="text/javascript" src="<?php echo base_url();?>/js/bootstrap.min.js"></script>
</body>

</html>

