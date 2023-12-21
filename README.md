VLIDATE FORM BY JAVA SCRIPT FUNCTION =>

function ValidateForm(){
    
   let flag1 = validateName("fnm");
   
   let flag2 = validateName("lnm");
   let flag3 = validateAge();
   let flag4 = validateGender();
   let flag5 = validateMobileNo();
 document.getElementById("errfnm").innerHTML = !flag1? "first name required minimum 3 characters!!!":"";
 document.getElementById("errlnm").innerHTML = !flag2? "last name required minimum 3 characters!!!":"";

 return flag1&&flag2&&flag3&&flag4&&flag5;
}

function validateName(name){
    let validname = document.getElementById(name).value;
    validname =   validname.trim();
    if(validname.length>=3)
        return true;
    
    return false;
}
function validateAge(){
    let dob = document.getElementById("dob").value;
    var today = new Date();
    var birthDate = new Date(dob);
    var age = today.getFullYear() - birthDate.getFullYear();
    document.getElementById("errdob").innerHTML = age>=21?"":"minimum age is 21!!!";
    if(age>=21)
    return true;
    return false;
}
function validateGender(){
    
   let arr = document.getElementsByName("gender");
   let  flag = false;
   for(var i=0; i<arr.length;i++){
    if(arr[i].checked){
        flag=true;
        break;
    }
   }
   document.getElementById("errgen").innerHTML = flag==false?"gender is required!!":" ";
   
   
   return flag;
}
function validateMobileNo(){
    let mobile = document.getElementById("mobile").value;
    let flag1 =false, flag2=false;
    if(mobile.match("[9876][0-9]{9}"))
    flag1=true;
flag2 = mobile.length==10?true:false;
  document.getElementById("errmob").innerHTML =   flag1&&flag2==true?"":"Invalid mobile number!!!";
 return  flag1&&flag2;
     
}
