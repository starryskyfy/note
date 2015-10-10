

## 冒泡排序
	
	<?php	
		function bubbleSort($arr){  
		  	$len = count($arr);
		    $temp = 0;
		 	for ($i = 0; $i < $len; $i++) { 
		  		for ($j = $i + 1; $j <$len ; $j++) { 
		  			if( $arr[$i] > $arr[$j] ) {
			  			$temp = $arr[$i];
			  			$arr[$i] = $arr[$j];
			  			$arr[$j] = $temp;
		  		    }
		  		}
		  	}
		  	return $arr;
		}
	?>
## 快速排序

	<?php
		function quickSort($arr) {
		    $len = count($arr);
		    if($len <= 1) {
		        return $arr;
		    }
		    $middle = $arr[0];//初始值为第一个数
		    $left = array(); //定义两个数组
		    $right = array(); 
		    for($i = 1; $i < $len; $i++) {
		        if($middle > $arr[$i]) {//arr[i]<middle,把arr[i]放入左边数组
		            $left[] = $arr[$i];
		        }
		        else {//arr[i]>middle,把arr[i]放入右边数组
		            $right[] = $arr[$i];
		        }
		    }
		    $left = quickSort($left);
		    $right = quickSort($right);
		    return array_merge($left,array($middle),$right);
		}
	?>
## 二分法查找

	<?php
		function binarySearch($arr,$value){ 
			$start = 0; 
			$end = count($arr) - 1; 
			
		/*	print_r($arr);
			
			echo "sdf: " . $value;*/
		
		
			while($start <= $end) {
			/*	echo "start: " . $start .", " . $end . "<br />"; */
				$index = intval(($start + $end) / 2);//index指向中间的数
				if($arr[$index] > $value) {//arr[index]>value,end指向index前一个数
					$end = $index - 1;
				} elseif($arr[$index] < $value) {
					$start = $index + 1; 
				} else{
					return $index; 
				} 
			}
			return -1;
		}
	?>
## 方法执行
		<?php
			$arr1 = array(1,6,5,9,8,2,7,3,4,0);
			$arr2 = array(1,6,5,9,8,2,7,3,4,0);
			$arr3 = array(1,3,6,9,11,20,26,37,41,48);  
			$v = 20;
			$arr1 = bubbleSort($arr1);
			foreach ($arr1 as $key => $value) {
				echo $value;
			}
			echo "<br>";
			$arr2 = quickSort($arr2);
			foreach ($arr2 as $key => $value) {
				echo $value;
			}
			echo "<br>";
			$k = binarySearch($arr3, $v);
				echo $k;
		?>  
