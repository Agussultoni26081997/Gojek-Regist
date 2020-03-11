<?php
date_default_timezone_set('Asia/Jakarta');
include "function.php";
echo color("green"," =================================== \n");
echo color("red"," **********************************  \n");

echo color("green"," Auto Create & Redeem Voucher \n");

echo color("green"," =================================== \n");
echo "   °°°°°°°°°°  MBAH OZIL  °°°°°°°°°°     \n";

echo " Time       : ".date('d-m-Y||H:i:s')." \n";
echo color("green"," =================================== \n");

//	function change(){
        $nama = nama();
        $email = str_replace(" ", "", $nama) . mt_rand(100, 999);
        ulang:
        echo color("nevy","?] NO HP: ");
        // $no = trim(fgets(STDIN));
        $nohp = trim(fgets(STDIN));
        $nohp = str_replace("62","62",$nohp);
        $nohp = str_replace("(","",$nohp);
        $nohp = str_replace(")","",$nohp);
        $nohp = str_replace("-","",$nohp);
        $nohp = str_replace(" ","",$nohp);

        if (!preg_match('/[^+0-9]/', trim($nohp))) {
            if (substr(trim($nohp),0,3)=='62') {
                $hp = trim($nohp);
            }
            else if (substr(trim($nohp),0,1)=='0') {
                $hp = '62'.substr(trim($nohp),1);
			}
			else if(substr(trim($nohp), 0, 2)=='62'){
				$hp = '6'.substr(trim($nohp), 1);
			}
			else{
				$hp = '1'.substr(trim($nohp),0,13);
			}
		}
		
		$data = '{"email":"'.$email.'@gmail.com","name":"'.$nama.'","phone":"+'.$hp.'","signed_up_country":"ID"}';
        $register = request("/v5/customers", null, $data);
        if(strpos($register, '"otp_token"')){
			$otptoken = getStr('"otp_token":"','"',$register);
			echo color("green","+] Verification code has been sent")."\n";
			otp:
			echo color("nevy","?] KODE OTP : ");
			$otp = trim(fgets(STDIN));
			$data1 = '{"client_name":"gojek:cons:android","data":{"otp":"' . $otp . '","otp_token":"' . $otptoken . '"},"client_secret":"83415d06-ec4e-11e6-a41b-6c40088ab51e"}';
			$verif = request("/v5/customers/phone/verify", null, $data1);
			if(strpos($verif, '"access_token"')){
				echo color("green","+] Register Success\n");
				$token = getStr('"access_token":"','"',$verif);
				$uuid = getStr('"resource_owner_id":',',',$verif);
				echo color("green","+] Your access token : ".$token."\n\n");
				save("token.txt",$token);
					}
				}
			}else{
				echo color("red","-] The code you entered is incorrect");
				echo color("green", "\n =================================== \n\n");
				echo color("yellow","!] Please input again \n");
				goto otp;
            }
		}else{
			echo color("red","-] This number already registered");
			echo color("green", "\n =================================== \n\n");
			echo color("yellow","!] Please register again using other number \n");
			goto ulang;
        }
//	}
// echo change()."\n";
