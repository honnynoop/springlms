echo "# springlms" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/honnynoop/springlms.git
git push -u origin main


# 1. 프로젝트 폴더에서
git init

# 2. 브랜치명을 main으로 설정
git branch -M main

# 3. 파일 추가
git add .

# 4. 커밋
git commit -m "Initial commit"

# 5. 원격 저장소 연결 (이미 연결되어 있으면 스킵)
git remote add origin https://github.com/honnynoop/springlms.git

# 6. push
git push -u origin main
