mkdir practice

// 깃 저장소를 다룰 새로운 폴더 생성 

git config --global user.name "yel-im"

git config --global user.email "choyr2016@naver.com"

// 사용자 이름과 이메일 전역 설정

cd practice

git init 

// 이 디렉토리에서 git을 사용한다 (만든 디렉토리 안에서 )

git remote add origin https://github.com/yel-im/Study-Network-and-Linux.git 

// 시스템 폴더와 저장소와 연결 해줌 

echo "# test" >> README.md  (= touch README.md -> vi "test") // README.md 파일에 test 입력

// 임의의 파일 생성 

git add README.md

git commit -m "first commit"

git push -u origin master
// 커밋