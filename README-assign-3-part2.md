```
https://github.com/opstree/spring3hibernate.git
*/master
```

```
#!/bin/bash
set -e

echo "🚀 Starting Java CI pipeline (Spring3Hibernate) with Java 11"

# ✅ Set JAVA_HOME to Temurin JDK 11
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export PATH=$JAVA_HOME/bin:$PATH

echo "Using Java from: $JAVA_HOME"
java -version
mvn -v

# 🧹 Clean, compile, test, and package
mvn clean package -Dmaven.compiler.source=11 -Dmaven.compiler.target=11 -DskipTests=false

# 🧾 Create HTML coverage/report directory
mkdir -p reports/htmlcov

# ✅ Copy reports if available (Jacoco / Surefire / site)
if [ -d "target/site/jacoco" ]; then
  cp -r target/site/jacoco/* reports/htmlcov/
elif [ -d "target/site" ]; then
  cp -r target/site/* reports/htmlcov/
fi

echo "✅ Java 11 build & test pipeline completed successfully!"
```


### Publish HTML Reports
<img width="1056" height="608" alt="image" src="https://github.com/user-attachments/assets/446a01ac-0a6f-42e7-abcc-507712a9588b" />

