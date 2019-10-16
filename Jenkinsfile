pipeline {
    agent any 
    tools { 
        maven "maven" 
        jdk "JDK8" 
    }    
    
    stages { 
        stage(' チェック アウト') { 
            steps { 
                // Git リポジトリ の 指定 
                git url: 'https://github.com/kirachki/Jenkins_Practical_Guide_3rd_Edition.git'
            } 
        } 
        
        stage(' Maven ビルド') { 
            steps { bat "mvn clean package" 
            }
        }
     
        stage(' テスト 結果 の 集計') { 
            steps {
                // JUnit テスト 結果 の 集計 
                junit(' target/surefire-reports/*.xml') 
                // JaCoCo 結果 の 集計 
                jacoco( execPattern: 'target/ jacoco. exec') 
            }
        }
                
        stage(' コード 解析 結果 の 集計') { 
            steps { 
                // Checkstyle 結果 の 集計 
                checkstyle( pattern: 'target/checkstyle-result.xml') 
                // FindBugs 結果 の 集計 
                findbugs( pattern:' target/findbugsXml.xml')
            }
        }
    }    
}

