var Web3 = require('web3');
var web3 = new Web3(new Web3.providers.HttpProvider());
var version = web3.version.api;

$.getJSON('https://api.bscscan.com/api?module=contract&action=getabi&address=0x0000000000000000000000000000000000001004&apikey=YourApiKeyToken', function (data) {
    var contractABI = "";
    contractABI = JSON.parse(data.result);
    if (contractABI != '') {
        var MyContract = web3.eth.contract(contractABI);
        var myContractInstance = MyContract.at("0xC96bfe23FeDD1edaD479dFe9464DDd5F56689769");
        var result = myContractInstance.memberId("0xfe8ad7dd2f564a877cc23feea6c0a9cc2e783715");
        console.log("result1 : " + result);
        var result = myContractInstance.members(1);
        console.log("result2 : " + result);
    } else {
        console.log("Error");
    }
});
