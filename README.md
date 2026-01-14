# 파일위치
C:\springlms\frontend>
C:\springlms\frontend>npm run dev --host

# 브라우저에서 열기:
LMS-COMPLETE-FINAL/frontend/index.html
```

---

## 🎯 주요 기능

✨ **완벽하게 구현된 기능들:**

### 🔐 인증 시스템
- JWT 기반 Access/Refresh Token
- BCrypt 비밀번호 암호화
- 로그인/회원가입/토큰 갱신

### 👥 사용자 관리
- 역할 기반 접근 제어 (ADMIN/USER)
- 사용자 정보 조회
- 관리자: 전체 사용자 목록

### 📚 시험 관리
- 시험 생성/조회/수정/삭제
- 카테고리별 분류
- 공개/비공개 설정
- 시간 제한, 합격 기준 설정

### ❓ 문제 은행
- 객관식/참거짓/단답형 문제
- 난이도 설정 (EASY/MEDIUM/HARD)
- 정답 및 해설 관리

### 📝 시험 응시
- 시험 응시 기록
- 자동 채점
- 결과 확인

### 📖 API 문서
- Swagger UI 통합
- 모든 API 테스트 가능

---

## 🔑 테스트 계정

### 관리자
- **Username**: `admin`
- **Password**: `admin123`
- **Email**: `admin@lms.com`

### 일반 사용자
- **Username**: `user1`
- **Password**: `admin123`
- **Email**: `user1@lms.com`

---

## 🌐 접속 URL

### 백엔드
- **API**: http://localhost:8080/api
- **Swagger UI**: http://localhost:8080/api/swagger-ui.html

### 프론트엔드
- **웹 앱**: 브라우저에서 `frontend/index.html` 열기

---

## 📊 기술 스택

- ☕ **Java 17**
- 🍃 **Spring Boot 3.4.5**
- 🔒 **Spring Security + JWT 0.12.6**
- 🗃️ **MyBatis 3.0.4**
- 🐬 **MySQL 8.0**
- 📝 **SpringDoc OpenAPI 2.8.3**
- 💚 **Vue.js 3**

---

## 💡 특징

✅ **완벽한 프로덕션 레벨 코드**
- 모든 레이어 완벽 구현 (Controller → Service → Mapper → XML)
- 예외 처리 및 검증
- 트랜잭션 관리

✅ **즉시 실행 가능**
- 설정 파일 완비
- 초기 데이터 포함
- 테스트 계정 제공

✅ **확장 가능한 구조**
- 클린 아키텍처
- RESTful API 설계
- 마이크로서비스 전환 가능

---

## 🎓 프로젝트 구조
```
LMS-COMPLETE-FINAL/
├── database/
│   └── schema.sql                 # DB 스키마 + 초기 데이터
│
├── backend/
│   ├── pom.xml                    # Maven 설정
│   └── src/main/
│       ├── java/com/lms/
│       │   ├── LmsApplication.java
│       │   ├── entity/            # 9개 Entity
│       │   ├── dto/               # 6개 DTO
│       │   ├── mapper/            # 5개 Mapper 인터페이스
│       │   ├── service/           # 2개 Service
│       │   ├── controller/        # 4개 Controller
│       │   ├── security/          # 3개 Security
│       │   └── config/            # 2개 Config
│       └── resources/
│           ├── application.yml    # 설정 파일
│           └── mapper/            # 4개 XML 매퍼
│
├── frontend/
│   └── index.html                 # Vue.js SPA
│
└── README.md                      # 완벽한 가이드



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


-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- -----------------------------------------------------
-- Schema mydb
-- -----------------------------------------------------
-- -----------------------------------------------------
-- Schema lms_exam_db
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema lms_exam_db
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `lms_exam_db` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci ;
USE `lms_exam_db` ;

-- -----------------------------------------------------
-- Table `lms_exam_db`.`categories`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`categories` (
  `category_id` BIGINT NOT NULL AUTO_INCREMENT,
  `category_name` VARCHAR(100) NOT NULL,
  `description` TEXT NULL DEFAULT NULL,
  `is_active` TINYINT(1) NULL DEFAULT '1',
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`category_id`),
  UNIQUE INDEX `category_name` (`category_name` ASC) VISIBLE)
ENGINE = InnoDB
AUTO_INCREMENT = 7
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `lms_exam_db`.`users`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`users` (
  `user_id` BIGINT NOT NULL AUTO_INCREMENT,
  `username` VARCHAR(50) NOT NULL,
  `password` VARCHAR(255) NOT NULL,
  `email` VARCHAR(100) NOT NULL,
  `full_name` VARCHAR(100) NOT NULL,
  `role` ENUM('ADMIN', 'USER') NULL DEFAULT 'USER',
  `is_active` TINYINT(1) NULL DEFAULT '1',
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `phone` VARCHAR(20) NULL DEFAULT NULL,
  PRIMARY KEY (`user_id`),
  UNIQUE INDEX `username` (`username` ASC) VISIBLE,
  UNIQUE INDEX `email` (`email` ASC) VISIBLE,
  INDEX `idx_username` (`username` ASC) VISIBLE,
  INDEX `idx_users_phone` (`phone` ASC) VISIBLE,
  INDEX `idx_users_email` (`email` ASC) VISIBLE)
ENGINE = InnoDB
AUTO_INCREMENT = 5
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `lms_exam_db`.`exams`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`exams` (
  `exam_id` BIGINT NOT NULL AUTO_INCREMENT,
  `exam_title` VARCHAR(200) NOT NULL,
  `category_id` BIGINT NOT NULL,
  `description` TEXT NULL DEFAULT NULL,
  `total_questions` INT NOT NULL DEFAULT '0',
  `total_points` INT NOT NULL DEFAULT '0',
  `duration_minutes` INT NULL DEFAULT '60',
  `passing_score` INT NULL DEFAULT '60',
  `is_published` TINYINT(1) NULL DEFAULT '0',
  `created_by` BIGINT NULL DEFAULT NULL,
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `is_active` TINYINT(1) NULL DEFAULT '0' COMMENT '시험 공개 여부 (사용자가 볼 수 있는지)',
  `exam_date` DATE NULL DEFAULT NULL COMMENT '시험 날짜',
  PRIMARY KEY (`exam_id`),
  INDEX `category_id` (`category_id` ASC) VISIBLE,
  INDEX `created_by` (`created_by` ASC) VISIBLE,
  INDEX `idx_exams_is_active` (`is_active` ASC) VISIBLE,
  INDEX `idx_exams_is_published` (`is_published` ASC) VISIBLE,
  CONSTRAINT `exams_ibfk_1`
    FOREIGN KEY (`category_id`)
    REFERENCES `lms_exam_db`.`categories` (`category_id`)
    ON DELETE CASCADE,
  CONSTRAINT `exams_ibfk_2`
    FOREIGN KEY (`created_by`)
    REFERENCES `lms_exam_db`.`users` (`user_id`)
    ON DELETE SET NULL)
ENGINE = InnoDB
AUTO_INCREMENT = 8
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `lms_exam_db`.`questions`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`questions` (
  `question_id` BIGINT NOT NULL AUTO_INCREMENT,
  `category_id` BIGINT NOT NULL,
  `question_text` TEXT NOT NULL,
  `question_type` ENUM('MULTIPLE_CHOICE', 'TRUE_FALSE', 'SHORT_ANSWER') NULL DEFAULT 'MULTIPLE_CHOICE',
  `difficulty` ENUM('EASY', 'MEDIUM', 'HARD') NULL DEFAULT 'MEDIUM',
  `points` INT NULL DEFAULT '10',
  `explanation` TEXT NULL DEFAULT NULL,
  `is_active` TINYINT(1) NULL DEFAULT '1',
  `created_by` BIGINT NULL DEFAULT NULL,
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`question_id`),
  INDEX `category_id` (`category_id` ASC) VISIBLE,
  INDEX `created_by` (`created_by` ASC) VISIBLE,
  CONSTRAINT `questions_ibfk_1`
    FOREIGN KEY (`category_id`)
    REFERENCES `lms_exam_db`.`categories` (`category_id`)
    ON DELETE CASCADE,
  CONSTRAINT `questions_ibfk_2`
    FOREIGN KEY (`created_by`)
    REFERENCES `lms_exam_db`.`users` (`user_id`)
    ON DELETE SET NULL)
ENGINE = InnoDB
AUTO_INCREMENT = 15
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `lms_exam_db`.`exam_questions`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`exam_questions` (
  `exam_question_id` BIGINT NOT NULL AUTO_INCREMENT,
  `exam_id` BIGINT NOT NULL,
  `question_id` BIGINT NOT NULL,
  `question_order` INT NOT NULL,
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`exam_question_id`),
  UNIQUE INDEX `uk_exam_question` (`exam_id` ASC, `question_id` ASC) VISIBLE,
  INDEX `question_id` (`question_id` ASC) VISIBLE,
  CONSTRAINT `exam_questions_ibfk_1`
    FOREIGN KEY (`exam_id`)
    REFERENCES `lms_exam_db`.`exams` (`exam_id`)
    ON DELETE CASCADE,
  CONSTRAINT `exam_questions_ibfk_2`
    FOREIGN KEY (`question_id`)
    REFERENCES `lms_exam_db`.`questions` (`question_id`)
    ON DELETE CASCADE)
ENGINE = InnoDB
AUTO_INCREMENT = 18
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `lms_exam_db`.`options`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`options` (
  `option_id` BIGINT NOT NULL AUTO_INCREMENT,
  `question_id` BIGINT NOT NULL,
  `option_text` TEXT NOT NULL,
  `option_order` INT NOT NULL,
  `is_correct` TINYINT(1) NULL DEFAULT '0',
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`option_id`),
  INDEX `question_id` (`question_id` ASC) VISIBLE,
  CONSTRAINT `options_ibfk_1`
    FOREIGN KEY (`question_id`)
    REFERENCES `lms_exam_db`.`questions` (`question_id`)
    ON DELETE CASCADE)
ENGINE = InnoDB
AUTO_INCREMENT = 29
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `lms_exam_db`.`question_statistics`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`question_statistics` (
  `stat_id` BIGINT NOT NULL AUTO_INCREMENT,
  `question_id` BIGINT NOT NULL,
  `total_attempts` INT NULL DEFAULT '0' COMMENT '총 응시 수',
  `correct_count` INT NULL DEFAULT '0' COMMENT '정답 수',
  `wrong_count` INT NULL DEFAULT '0' COMMENT '오답 수',
  `correct_rate` DECIMAL(5,2) NULL DEFAULT '0.00' COMMENT '정답률 (%)',
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`stat_id`),
  UNIQUE INDEX `unique_question_stat` (`question_id` ASC) VISIBLE,
  CONSTRAINT `question_statistics_ibfk_1`
    FOREIGN KEY (`question_id`)
    REFERENCES `lms_exam_db`.`questions` (`question_id`)
    ON DELETE CASCADE)
ENGINE = InnoDB
AUTO_INCREMENT = 31
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci
COMMENT = '문제별 통계';


-- -----------------------------------------------------
-- Table `lms_exam_db`.`user_exams`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`user_exams` (
  `user_exam_id` BIGINT NOT NULL AUTO_INCREMENT,
  `user_id` BIGINT NOT NULL,
  `exam_id` BIGINT NOT NULL,
  `started_at` TIMESTAMP NULL DEFAULT NULL,
  `submitted_at` TIMESTAMP NULL DEFAULT NULL,
  `score` INT NULL DEFAULT '0',
  `total_questions` INT NOT NULL,
  `correct_answers` INT NULL DEFAULT '0',
  `wrong_answers` INT NULL DEFAULT '0',
  `status` ENUM('NOT_STARTED', 'IN_PROGRESS', 'SUBMITTED', 'GRADED') NULL DEFAULT 'NOT_STARTED',
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`user_exam_id`),
  UNIQUE INDEX `uk_user_exam` (`user_id` ASC, `exam_id` ASC) VISIBLE,
  INDEX `exam_id` (`exam_id` ASC) VISIBLE,
  CONSTRAINT `user_exams_ibfk_1`
    FOREIGN KEY (`user_id`)
    REFERENCES `lms_exam_db`.`users` (`user_id`)
    ON DELETE CASCADE,
  CONSTRAINT `user_exams_ibfk_2`
    FOREIGN KEY (`exam_id`)
    REFERENCES `lms_exam_db`.`exams` (`exam_id`)
    ON DELETE CASCADE)
ENGINE = InnoDB
AUTO_INCREMENT = 19
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `lms_exam_db`.`user_answers`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `lms_exam_db`.`user_answers` (
  `answer_id` BIGINT NOT NULL AUTO_INCREMENT,
  `user_exam_id` BIGINT NOT NULL,
  `question_id` BIGINT NOT NULL,
  `selected_option_id` BIGINT NULL DEFAULT NULL,
  `answer_text` TEXT NULL DEFAULT NULL,
  `is_correct` TINYINT(1) NULL DEFAULT '0',
  `created_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`answer_id`),
  INDEX `user_exam_id` (`user_exam_id` ASC) VISIBLE,
  INDEX `question_id` (`question_id` ASC) VISIBLE,
  INDEX `selected_option_id` (`selected_option_id` ASC) VISIBLE,
  CONSTRAINT `user_answers_ibfk_1`
    FOREIGN KEY (`user_exam_id`)
    REFERENCES `lms_exam_db`.`user_exams` (`user_exam_id`)
    ON DELETE CASCADE,
  CONSTRAINT `user_answers_ibfk_2`
    FOREIGN KEY (`question_id`)
    REFERENCES `lms_exam_db`.`questions` (`question_id`)
    ON DELETE CASCADE,
  CONSTRAINT `user_answers_ibfk_3`
    FOREIGN KEY (`selected_option_id`)
    REFERENCES `lms_exam_db`.`options` (`option_id`)
    ON DELETE SET NULL)
ENGINE = InnoDB
AUTO_INCREMENT = 31
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;


-- 초기 데이터
INSERT INTO users (username, password, email, full_name, role,phone) VALUES
('admin', '$2a$10$9uhSB/R2YZHIB3bvWGQeQeNgIRrN4pAM.JjFqnteErYepbBJ0EI86', 'admin@lms.com', '어드민', 'ADMIN', '010-1234-1234'),
('user1', '$2a$10$9uhSB/R2YZHIB3bvWGQeQeNgIRrN4pAM.JjFqnteErYepbBJ0EI86', 'user1@lms.com', '홍길동', 'USER','010-1234-1235'),
('user2', '$2a$10$9uhSB/R2YZHIB3bvWGQeQeNgIRrN4pAM.JjFqnteErYepbBJ0EI86', 'user2@lms.com', '장길산', 'USER', '010-1234-1236'),
('user3', '$2a$10$9uhSB/R2YZHIB3bvWGQeQeNgIRrN4pAM.JjFqnteErYepbBJ0EI86', 'user3@lms.com', '임꺽정', 'USER', '010-1234-1234');


INSERT INTO categories (category_name, description) VALUES
('Java 프로그래밍', 'Java 기초부터 고급까지'),
('Spring Framework', 'Spring Boot, Spring MVC'),
('데이터베이스', 'SQL, MySQL'),
('알고리즘', '자료구조와 알고리즘'),
('웹 개발', 'HTML, CSS, JavaScript');

INSERT INTO questions (category_id, question_text, question_type, difficulty, points, explanation, created_by) VALUES
(1, 'Java에서 main 메서드의 올바른 선언은?', 'MULTIPLE_CHOICE', 'EASY', 10, 'main 메서드는 public static void main(String[] args) 형태입니다.', 1);

INSERT INTO question_options (question_id, option_text, option_order, is_correct) VALUES
(1, 'public static void main(String[] args)', 1, TRUE),
(1, 'public void main(String[] args)', 2, FALSE),
(1, 'static void main(String[] args)', 3, FALSE),
(1, 'public main(String[] args)', 4, FALSE);

commit;

USE lms_exam_db;
show tables;
select * from users;

update exams set exam_date='2026-01-06' where exam_id=2;
delete from user_exams where user_exam_id=2;

select * from users;
select * from exams;
select * from user_exams;
select * from questions;
ALTER TABLE users 
ADD COLUMN phone VARCHAR(20);

-- 인덱스 추가
CREATE INDEX idx_users_phone ON users(phone);
CREATE INDEX idx_users_email ON users(email);

-- 제약조건 추가
ALTER TABLE users
ADD CONSTRAINT chk_phone_format 
CHECK (phone IS NULL OR phone REGEXP '^[0-9-+() ]+$');

