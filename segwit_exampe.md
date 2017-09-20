# Bitcoin core segwit example:
create 2 of 2 multisig address

```
address 1: mmDjiCXo77cSRsS4SLXYi9NzARRezTsGrm
address 2: n4Wq5d2pEb7tt8F8JPKvu3AtySCCoA6d1F
```
```
bitcoin-cli createmultisig 2 "[\"mmDjiCXo77cSRsS4SLXYi9NzARRezTsGrm\",\"n4Wq5d2pEb7tt8F8JPKvu3AtySCCoA6d1F\"]"

{
  "address": "2N7vEVrGo14DxSaRajv7pmokZA6j8LK5szi",
  "redeemScript": "522103dff1141f6d504522febd0e4f0dffc85f62b0209ac605a8c34939b85c471996ba2102084d73db861448ef195b5bf6c465f7f4957c6e8328dbcbe7bd799792810ed39852ae"
}
```
fund address:
```
bitcoin@vps457928:~$ bitcoin-cli decoderawtransaction 0200000001e1479b8a4347b231154031d3fb045433e13324b23672c507d57778b1540dce55000000004847304402203f083168613dd072adfef41288a1a0f1a7daf28053d77ce2951e26a645b82d530220240988496ecde3f21c0ff8318720f3c80fa457fdaef8d7a400ef7d0d593d5f1f01feffffff0228021024010000001976a914004ddcad32bd09e977d3789a24fe3f5a46e50c9788ac00e1f5050000000017a914a0f268b5187e8cfa102b2fffa2825002d15c732a8765000000

{
  "txid": "5276cb0462e8b0f1b82da6183485e73a9f4a1a6c995d0755cfcf90f001fb1877",
  "hash": "5276cb0462e8b0f1b82da6183485e73a9f4a1a6c995d0755cfcf90f001fb1877",
  "version": 2,
  "size": 189,
  "vsize": 189,
  "locktime": 101,
  "vin": [
    {
      "txid": "55ce0d54b17877d507c57236b22433e1335404fbd331401531b247438a9b47e1",
      "vout": 0,
      "scriptSig": {
        "asm": "304402203f083168613dd072adfef41288a1a0f1a7daf28053d77ce2951e26a645b82d530220240988496ecde3f21c0ff8318720f3c80fa457fdaef8d7a400ef7d0d593d5f1f[ALL]",
        "hex": "47304402203f083168613dd072adfef41288a1a0f1a7daf28053d77ce2951e26a645b82d530220240988496ecde3f21c0ff8318720f3c80fa457fdaef8d7a400ef7d0d593d5f1f01"
      },
      "sequence": 4294967294
    }
  ],
  "vout": [
    {
      "value": 48.99996200,
      "n": 0,
      "scriptPubKey": {
        "asm": "OP_DUP OP_HASH160 004ddcad32bd09e977d3789a24fe3f5a46e50c97 OP_EQUALVERIFY OP_CHECKSIG",
        "hex": "76a914004ddcad32bd09e977d3789a24fe3f5a46e50c9788ac",
        "reqSigs": 1,
        "type": "pubkeyhash",
        "addresses": [
          "mfYZa14WbpP2v8Yq4oeMqTvARtoBGC91JC"
        ]
      }
    },
    {
      "value": 1.00000000,
      "n": 1,
      "scriptPubKey": {
        "asm": "OP_HASH160 a0f268b5187e8cfa102b2fffa2825002d15c732a OP_EQUAL",
        "hex": "a914a0f268b5187e8cfa102b2fffa2825002d15c732a87",
        "reqSigs": 1,
        "type": "scripthash",
        "addresses": [
          "2N7vEVrGo14DxSaRajv7pmokZA6j8LK5szi"
        ]
      }
    }
  ]
}
```
```
bitcoin@vps457928:~$ bitcoin-cli validateaddress 2N7vEVrGo14DxSaRajv7pmokZA6j8LK5szi
{
  "isvalid": true,
  "address": "2N7vEVrGo14DxSaRajv7pmokZA6j8LK5szi",
  "scriptPubKey": "a914a0f268b5187e8cfa102b2fffa2825002d15c732a87",
  "ismine": true,
  "iswatchonly": false,
  "isscript": true,
  "script": "multisig",
  "hex": "522103dff1141f6d504522febd0e4f0dffc85f62b0209ac605a8c34939b85c471996ba2102084d73db861448ef195b5bf6c465f7f4957c6e8328dbcbe7bd799792810ed39852ae",
  "addresses": [
    "mmDjiCXo77cSRsS4SLXYi9NzARRezTsGrm",
    "n4Wq5d2pEb7tt8F8JPKvu3AtySCCoA6d1F"
  ],
  "sigsrequired": 2,
  "account": ""
}
```
create segwit address:
```
bitcoin@vps457928:~/.bitcoin/regtest$ bitcoin-cli addwitnessaddress 2N7vEVrGo14DxSaRajv7pmokZA6j8LK5szi
2NEJY5jwa7SGBNjKoAhnoTNT17jyNKm5cCy
bitcoin@vps457928:~/.bitcoin/regtest$ bitcoin-cli validateaddress 2NEJY5jwa7SGBNjKoAhnoTNT17jyNKm5cCy
{
  "isvalid": true,
  "address": "2NEJY5jwa7SGBNjKoAhnoTNT17jyNKm5cCy",
  "scriptPubKey": "a914e6fafe5802f7f9e09f2520d017bd53f95a55b21f87",
  "ismine": true,
  "iswatchonly": false,
  "isscript": true,
  "script": "witness_v0_scripthash",
  "hex": "00207729415d3a802c47c1dfa73ab32e1e3a2ebaaf39a6d8a48542c3c091e5f9432f",
  "addresses": [
  ],
  "account": ""
}
```
funding transaction
```
{
  "txid": "499f33b6fc1b23b17a501131bc117dcca7af497e73e646f0371730651cd3e6f6",
  "hash": "499f33b6fc1b23b17a501131bc117dcca7af497e73e646f0371730651cd3e6f6",
  "version": 2,
  "size": 190,
  "vsize": 190,
  "locktime": 1201,
  "vin": [
    {
      "txid": "20d1fe950c4a1547a3494fb8672e41dbf0bbfd3d2ded3b879c1addafffd245dd",
      "vout": 0,
      "scriptSig": {
        "asm": "3045022100da4d7f5b1144f29bf7354a71b60afd4006ba498fdc6c9bfa06aacc0aafa4c44e022058ffba86ac24d65c92cde5f3c4f8b3f51f23bbdfc9964b2c12596eba5beef7f5[ALL] 02360f0c7e3d19f196c8304431953ea7bc11612b5fa2c0dbfbabad30b25c7f1c20",
        "hex": "483045022100da4d7f5b1144f29bf7354a71b60afd4006ba498fdc6c9bfa06aacc0aafa4c44e022058ffba86ac24d65c92cde5f3c4f8b3f51f23bbdfc9964b2c12596eba5beef7f5012102360f0c7e3d19f196c8304431953ea7bc11612b5fa2c0dbfbabad30b25c7f1c20"
      },
      "sequence": 4294967294
    }
  ],
  "vout": [
    {
      "value": 0.99990120,
      "n": 0,
      "scriptPubKey": {
        "asm": "OP_HASH160 e6fafe5802f7f9e09f2520d017bd53f95a55b21f OP_EQUAL",
        "hex": "a914e6fafe5802f7f9e09f2520d017bd53f95a55b21f87",
        "reqSigs": 1,
        "type": "scripthash",
        "addresses": [
          "2NEJY5jwa7SGBNjKoAhnoTNT17jyNKm5cCy"
        ]
      }
    }
  ],
  "hex": "0200000001dd45d2ffafdd1a9c873bed2d3dfdbbf0db412e67b84f49a347154a0c95fed120000000006b483045022100da4d7f5b1144f29bf7354a71b60afd4006ba498fdc6c9bfa06aacc0aafa4c44e022058ffba86ac24d65c92cde5f3c4f8b3f51f23bbdfc9964b2c12596eba5beef7f5012102360f0c7e3d19f196c8304431953ea7bc11612b5fa2c0dbfbabad30b25c7f1c20feffffff0168baf5050000000017a914e6fafe5802f7f9e09f2520d017bd53f95a55b21f87b1040000"
}
```
check outputs:
```
bitcoin@vps457928:~/.bitcoin/regtest$ bitcoin-cli listunspent
[
  {
    "txid": "499f33b6fc1b23b17a501131bc117dcca7af497e73e646f0371730651cd3e6f6",
    "vout": 0,
    "address": "2NEJY5jwa7SGBNjKoAhnoTNT17jyNKm5cCy",
    "account": "",
    "redeemScript": "00207729415d3a802c47c1dfa73ab32e1e3a2ebaaf39a6d8a48542c3c091e5f9432f",
    "scriptPubKey": "a914e6fafe5802f7f9e09f2520d017bd53f95a55b21f87",
    "amount": 0.99990120,
    "confirmations": 6,
    "spendable": true,
    "solvable": true,
    "safe": true
  }
]
```
spend P2SH-P2WSH
```
bitcoin@vps457928:~/.bitcoin/regtest$ bitcoin-cli getrawtransaction e0368f047849fd926aeab69756e3c1b00bbadcd292f592d4f1e1a55d6f22b6b2 true
{
  "txid": "e0368f047849fd926aeab69756e3c1b00bbadcd292f592d4f1e1a55d6f22b6b2",
  "hash": "40b9ebe1c5e8fe391cf82262f0cbc72fc27f530babc745b8c2cab379ad7bf4ba",
  "version": 2,
  "size": 340,
  "vsize": 175,
  "locktime": 1207,
  "vin": [
    {
      "txid": "499f33b6fc1b23b17a501131bc117dcca7af497e73e646f0371730651cd3e6f6",
      "vout": 0,
      "scriptSig": {
        "asm": "00207729415d3a802c47c1dfa73ab32e1e3a2ebaaf39a6d8a48542c3c091e5f9432f",
        "hex": "2200207729415d3a802c47c1dfa73ab32e1e3a2ebaaf39a6d8a48542c3c091e5f9432f"
      },
      "txinwitness": [
        "",
        "30440220242be954289c86c19622541a536a3d0763d47da10f34ca7263231a89c5c6b735022070cde92f50303ec96324f87e5822cc2c5e85916b44d1402b174cf174e1711ddf01",
        "304402202455df2681c4470e4306fd608e55ca6284d5bdcf574aff6b2b02090b1669a70802203548755dc69488408bb2fbf6fc48136775b7d178b69495235b7cff0acbef61d301",
        "522103dff1141f6d504522febd0e4f0dffc85f62b0209ac605a8c34939b85c471996ba2102084d73db861448ef195b5bf6c465f7f4957c6e8328dbcbe7bd799792810ed39852ae"
      ],
      "sequence": 4294967294
    }
  ],
  "vout": [
    {
      "value": 0.99986600,
      "n": 0,
      "scriptPubKey": {
        "asm": "OP_DUP OP_HASH160 84e5d7f43a1ffa0f8592d8c11583d8fef96fda21 OP_EQUALVERIFY OP_CHECKSIG",
        "hex": "76a91484e5d7f43a1ffa0f8592d8c11583d8fef96fda2188ac",
        "reqSigs": 1,
        "type": "pubkeyhash",
        "addresses": [
          "msdeqBnu8XyqfvCNCbRQU9S9fEdXj1Ddq8"
        ]
      }
    }
  ],
  "hex": "02000000000101f6e6d31c65301737f046e6737e49afa7cc7d11bc3111507ab1231bfcb6339f4900000000232200207729415d3a802c47c1dfa73ab32e1e3a2ebaaf39a6d8a48542c3c091e5f9432ffeffffff01a8acf505000000001976a91484e5d7f43a1ffa0f8592d8c11583d8fef96fda2188ac04004730440220242be954289c86c19622541a536a3d0763d47da10f34ca7263231a89c5c6b735022070cde92f50303ec96324f87e5822cc2c5e85916b44d1402b174cf174e1711ddf0147304402202455df2681c4470e4306fd608e55ca6284d5bdcf574aff6b2b02090b1669a70802203548755dc69488408bb2fbf6fc48136775b7d178b69495235b7cff0acbef61d30147522103dff1141f6d504522febd0e4f0dffc85f62b0209ac605a8c34939b85c471996ba2102084d73db861448ef195b5bf6c465f7f4957c6e8328dbcbe7bd799792810ed39852aeb7040000",
  "blockhash": "0a34f3d8c1ea06c95e0abb895275bb53b2601fc8d27edcbc5132cb265f3b680e",
  "confirmations": 6,
  "time": 1505944081,
  "blocktime": 1505944081
}
```


