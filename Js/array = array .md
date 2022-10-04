### array = array2


array = array2 

는 왼쪽을 오른쪽으로 만들어라 ! 가아니라 

왼쪽 오른쪽 값을 공유해라 라는 말이됨 

그래서 array = array2 가 같아지게 됨 

array2 = array가 된단 말임 

array2를 수정해도 array 가 되고 

array를 수정해도 array2 가 된다 



고로 원래 의도대로 하고싶다면

array = [...array2]

로 해야된다.


처음 방식대로 하면 원본을 보존할수가없다! 





