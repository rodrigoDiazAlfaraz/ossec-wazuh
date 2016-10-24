/**
 * Jenkinsfile for OSSEC Wazuh
 * Copyright (C) 2016 Wazuh Inc.
 * June 22, 2016.
 *
 * This program is a free software; you can redistribute it
 * and/or modify it under the terms of the GNU General Public
 * License (version 2) as published by the FSF - Free Software
 * Foundation.
 */

node {
    
    //Stage checkout source
    stage name: 'Checkout source', concurrency: 1
    
    checkout scm
    sh 'sudo apt-get update'
    
   
    
    //Stage windows compilation
    stage name: 'Windows compilation', concurrency: 1
    
    dir ('src') {
        sh 'sudo apt-get -y install aptitude && sudo aptitude -y install mingw-w64 nsis'
        sh 'sudo make --warn-undefined-variables TARGET=winagent'
        sh 'sudo make clean && sudo rm -rf /var/ossec/'
    }
    
}
