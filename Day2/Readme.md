### Fabric Test Network commands 

Note: Open a terminal in the KBA-CHF Folder & Execute the Following Commands

`curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh && chmod +x install-fabric.sh`

`./install-fabric.sh -f '2.5.12' -c '1.5.15'`

`sudo cp fabric-samples/bin/* /usr/local/bin`

## To use the script navigate to test-network folder inside the fabric-samples folder,

`cd fabric-samples/test-network/`

`./network.sh -h`

`./network.sh up createChannel`

`docker ps -a`

### Deploy asset-transfer basic sample chaincode listed in the samples.

`./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go -ccl go`

```
export FABRIC_CFG_PATH=$PWD/../config/


export CORE_PEER_TLS_ENABLED=true


export CORE_PEER_LOCALMSPID="Org1MSP"

export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt

export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp

export CORE_PEER_ADDRESS=localhost:7051

```

`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"InitLedger","Args":[]}'`


`peer chaincode query -C mychannel -n basic -c '{"Args":["GetAllAssets"]}'`


`peer chaincode query -C mychannel -n basic -c '{"function":"ReadAsset","Args":["asset5"]}'`

### For KBA-Automobile Application

`cd addOrg3`

`./addOrg3.sh up`

`cd ..`

Note: Create a New Folder name it as KBA-Automobile within the Fabric samples directory and copy our own  Chaincode folder to KBA-Automobile folder.
Create collection.json file with  MSPID's as Org1MSP and Org2MSP.

` ./network.sh deployCC -ccn Automobile -ccp ../KBA-Automobile/Chaincode/ -ccl  go -cccg ../KBA-Automobile/Chaincode/collection-minifab.json`

### Open a new terminal consider as peer0.org2 terminal

```
export FABRIC_CFG_PATH=$PWD/../config/
export CORE_PEER_TLS_ENABLED=true
export CORE_PEER_LOCALMSPID="Org2MSP"
export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt
export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp
export CORE_PEER_ADDRESS=localhost:9051

```

### Open a new terminal consider as peer0.org3 terminal

```
export FABRIC_CFG_PATH=$PWD/../config/
export CORE_PEER_TLS_ENABLED=true
export CORE_PEER_LOCALMSPID="Org3MSP"
export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org3.example.com/peers/peer0.org3.example.com/tls/ca.crt
export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org3.example.com/users/Admin@org3.example.com/msp
export CORE_PEER_ADDRESS=localhost:11051

```
### peer0.org1 terminal (Host terminal)



`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"CreateCar","Args":["Car-01", "Tata", "Tiago", "White", "Factory-1", "22/07/2023" ]}'`

`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"CreateCar","Args":["Car-02", "Tata", "Punch", "White", "Factory-1", "22/07/2023" ]}'`

`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"CreateCar","Args":["Car-03", "Tata", "Altroz", "Red", "Factory-1", "10/07/2020" ]}'`

`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"CreateCar","Args":["Car-04", "Tata", "Tiago", "Blue", "Factory-4", "18/09/2023" ]}'`



`peer chaincode query -C mychannel -n Automobile -c '{"function":"ReadCar","Args":["Car-01"]}'`

`peer chaincode query -C mychannel -n Automobile -c '{"Args":["CarContract:GetCarsByRange", "Car-01", "Car-04"]}'`

`peer chaincode query -C mychannel -n Automobile -c '{"Args":["CarContract:GetCarHistory", "Car-01"]}'`


### peer0.org2 terminal
```
export MAKE=$(echo -n "Tata" | base64 | tr -d \\n)
export MODEL=$(echo -n "Tiago" | base64 | tr -d \\n)
export COLOR=$(echo -n "White" | base64 | tr -d \\n)
export DEALER_NAME=$(echo -n "Popular" | base64 | tr -d \\n)
```


`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"Args":["OrderContract:CreateOrder","ORD-01"]}' --transient "{\"make\":\"$MAKE\",\"model\":\"$MODEL\",\"color\":\"$COLOR\",\"dealerName\":\"$DEALER_NAME\"}"`

`peer chaincode query -C mychannel -n Automobile -c '{"Args":["OrderContract:ReadOrder","ORD-01"]}'`

`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"MatchOrder","Args":["Car-01", "ORD-01"]}'`

### peer0.org3 terminal

`peer chaincode query -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" -c '{"function":"ReadCar","Args":["Car-01"]}'`

`peer chaincode query -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt"  -c '{"Args":["OrderContract:ReadOrder","ORD-01"]}'`

`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"RegisterCar","Args":["Car-01","Bob","KL-01-7777"]}'`

`peer chaincode query -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" -c '{"function":"ReadCar","Args":["Car-01"]}'`

`peer chaincode query -C mychannel -n Automobile --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" -c '{"function":"GetCarHistory","Args":["Car-01"]}'`


### Stopping the network

`cd addOrg3`

`./addOrg3.sh down`

`cd ..`

`./network.sh down`
















