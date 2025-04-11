
```
╔══════════════════╗       ╔════════════════════════╗
║    students      ║<--+---║  attendance_records    ║
╚══════════════════╝   │   ╚════════════════════════╝
║ uuid id (PK)     ║   │   ║ uuid id (PK)           ║
║ name, email      ║   │   ║ student_id (FK)        ║
║ roll_number      ║   │   ║ date, status           ║
║ course, semester ║   │   ║ created_at, updated_at ║
║ scores, cgpa     ║   │   ╚════════════════════════╝
║ avatar_url       ║   │
╚══════════════════╝   │   ╔════════════════════════╗
                        +---║ behavioral_incidents   ║
                            ╚════════════════════════╝
                            ║ id (PK), student_id FK ║
                            ║ incident_date          ║
                            ║ type, description      ║
                            ║ severity               ║
                            ╚════════════════════════╝

                            ╔════════════════════════╗
                            ║  personality_traits     ║
                            ╚════════════════════════╝
                            ║ id (PK), student_id FK ║
                            ║ openness, etc.         ║
                            ╚════════════════════════╝

                            ╔════════════════════════╗
                            ║     notifications       ║
                            ╚════════════════════════╝
                            ║ id (PK), student_id FK ║
                            ║ title, message         ║
                            ║ recipient_id/role      ║
                            ╚════════════════════════╝

                            ╔════════════════════════╗
                            ║    student_materials    ║
                            ╚════════════════════════╝
                            ║ id (PK)                ║
                            ║ student_id FK          ║
                            ║ material_id FK         ║
                            ╚════════════════════════╝


╔══════════════════╗       ╔════════════════════════╗
║  course_cards    ║<--+---║   course_materials     ║
╚══════════════════╝   │   ╚════════════════════════╝
║ id (PK)          ║   │   ║ id (PK), course_card FK║
║ title, subject   ║   │   ║ file_url, file_type    ║
║ instructor, etc. ║   │   ╚════════════════════════╝
╚══════════════════╝   │
                       +---╔════════════════════════╗
                           ║  student_materials      ║
                           ╚════════════════════════╝

╔══════════════════╗       ╔════════════════════════╗
║     users        ║<--+---║        profiles         ║
╚══════════════════╝   │   ╚════════════════════════╝
║ id (PK)          ║   │   ║ id (PK), user_id (FK)  ║
║ username, email  ║   │   ║ avatar, bio, timestamps║
╚══════════════════╝   │   ╚════════════════════════╝

╔══════════════════╗
║   faculty        ║
╚══════════════════╝
║ id (PK), name    ║
║ dept, email      ║
║ chat_enabled     ║
╚══════════════════╝

╔══════════════════╗
║  admin_users     ║
╚══════════════════╝
║ id (PK), email   ║
║ phone, password  ║
╚══════════════════╝

╔══════════════════╗
║    messages      ║
╚══════════════════╝
║ id (PK)          ║
║ sender_id FK     ║
║ receiver_id FK   ║
║ content, read    ║
╚══════════════════╝

╔══════════════════╗
║ teaching_materials║
╚══════════════════╝
║ id (PK), course  ║
║ shared_with_all  ║
║ shared_with_course║
╚══════════════════╝

╔══════════════════╗
║     sessions     ║
╚══════════════════╝
║ sid (PK)         ║
║ json sess        ║
║ expire timestamp ║
╚══════════════════╝
```
