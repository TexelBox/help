# FREQUENTLY ASKED QUESTIONS & OTHER USEFUL TIPS/REMINDERS
- **[HOW DO I SKIP CONTINUOUS INTEGRATION ON THE NEXT COMMIT?](#how-do-i-skip-continuous-integration-on-the-next-commit)**

---

#### HOW DO I SKIP CONTINUOUS INTEGRATION ON THE NEXT COMMIT?
- Skip all...
```
git commit -m "[skip ci] message"
```
- Skip AppVeyor only...
```
git commit -m "[skip appveyor] message"
```
- Skip Travis CI only...
```
git commit -m "[skip travis] message"
```

---
