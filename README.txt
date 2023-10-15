// ignore_for_file: avoid_print

import 'package:crypto_keys/crypto_keys.dart';
import 'dart:typed_data';
import 'dart:convert';
import 'package:cryptography/cryptography.dart';
import 'package:cryptography/dart.dart';
import 'package:rsa_encrypt/rsa_encrypt.dart';
import 'package:pointycastle/asymmetric/api.dart';

String aesEncryptedKey =
    "UegZvQTJZfvSQprH8rlfHtoUFGa/Eh6rgf0aEHA0+dSHTBQpPFfS2Zc3x26zB8y1yqvooaEpCGpWX+KBaP+p5jidUHZA6GDl3eRxRkLv0T+xkxnLfW7rd5Lnp+QJ3VFBUkzEyiqh1jtCpPM1j0ZfBi6ZiEmQdxKkfQ0m6UhvhkFIkLR9mpA6WIGZ/ojjvgV+NaKZbXQQrpVzJMqY9h8TIzUl0mgLgmrDLDKGycfNv8+GrL9a8Y2Tgv/jm6XO+RzM+xk54ldLjiffjEpZUi/ELJJYklfEbL3FCau/JTW10JzJOp8WmRLZ7R0HLePIO/pvEHNayES2LuWMiI1GQpbnKQ==";
String rsaPublicKey =
    "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAhEmKd6JLhtKz3cpqktyj189dTxYIvxE6i7kHEPQQ+7HXX8M8FxOB+ZXyppHQSgVGNksJZ0M62yaP0fjRwSCp/15RvGetPkVPIUXFi1LYxEwv5L/SrJ+xgdBd3JcckvgoppJb+Bp4437fcZAvXrNPRi0Dim908aWL82Pvd5sr2PTRojezdh8RoES2HpX253xMOOBG8miCJOLsifYZBRW8oWM6sfsu3CEKyaJUN0jkf4qKCMNzBlqmLFRoPNf3e9p94nOLqZLhfCrvEjj/KCLrrtKEMNycbloJZiEfjtfCmk86Z5g7wqmU3kv5wX2mSQeY5rs0fGSBpyLlviwCt7vSUQIDAQAB";

String json =
    '{"rejectTradeOnFailure":false,"tradeLegs":[{"legIndex":1,"contractIds":[13],"price":10.5,"strikePrice":1,"quantity":22,"executionDateTime":"2023-10-13T16:25:50.706193700","tradingSession":"T+1","tradeType":"OTC","seller":{"accountId":2,"brokerId":5,"traderName":"TC1","internalTradeId":"123","comment":"comment"},"allegedSeller":null,"buyer":{"accountId":1,"brokerId":4,"traderName":"TC1","internalTradeId":"123","comment":"comment"},"allegedBuyer":null,"flexExpiry":null}]}';

String payload =
    'hr2+nsLLT4RTfg1rjjIswVK4PZLoU3t8JnYdB+AkNFQZH82x6xVgh3+C1tPmAEsfDC8hJQOi878s/En+HohnGgih+0dYudr0Y9Q2ag7c7pBDcXP3CoIurBY9Tkh1hTxg+FiN3OapD3q6Z4Te2Oqpoe6ci8Pw84TdWfAQWREF03GvTRK1b3R7s8jHIBkhdZbWM9xqCkb7+pgaVOHJ74WenkMmli2TD+vG2p7MMXD2MPuHReTa2/YjoMduAP9MY0QdY+V3N8sHaESwvnuwnxl1ovxb1RePKP9PBZHxH4h7D1f/YhyHa3v80iKREeoDtd8EhZTSOc4cbsYKM2l54n5A2KDUki7wreepGoR9dmQolfjdeB7FG9FuxTzEIhW7E5/ygQvsMMBGKQhx0MO0IXYk3BWvNYwScgmlPWBtEwZ29Q1RmGEa6kSxcU3TyBUGEVKL+vD62YaQMmoI5TIRwloDzD+ttNrbf1bizCPiZYWjBkjGdgLRUPxPy7Hv4ibuQjrjv996ss7eaw+Lwvz+24QsRbIK5ZmCurjH0/pl194STCO+Tebhz+7Xgw1VC4TLJZKgFD86HpHeAsjQw66FrCU0ICWkBRx+X8pcyBx1B1xydNNTKgRcHO4rmimFTLjsYgLR';

void main() async {
  final type = DartRsaSsaPkcs1v15(Sha256()).keyPairType;

  final publicKey = SimplePublicKey(base64Decode(rsaPublicKey), type: type);
  print(publicKey);

  var a = DartRsaSsaPkcs1v15(Sha256());

  // RSAPublicKey k = RsaKeyHelper().parsePublicKeyFromPem(rsaPublicKey);
  // print(k);

  RSAPublicKey k = AsymmetricBlockCipher('RSA/SomeEncodingHere');

// final publicKey = RSAKeyParser().parse(myPublicKey) as RSAPublicKey;

  // SymmetricKey key = SymmetricKey(keyValue: '');

  // KeyPair.symmetric(key);

  // // Generate a new random symmetric key pair
  // var keyPair = KeyPair.generateSymmetric(128);
  // // Use the public key to create an encrypter with the AES/GCM algorithm
  // var encrypter = keyPair.publicKey.createEncrypter(algorithms.encryption.aes.gcm);
  // // Encrypt the content with an additional authentication data for integrity
  // // protection
  // var content = "A very secret text";
  // var aad = "It is me";
  // var v = encrypter.encrypt(Uint8List.fromList(content.codeUnits),
  //     additionalAuthenticatedData: Uint8List.fromList(aad.codeUnits));
  // print("Encrypting '$content'");
  // print("Ciphertext: ${v.data}");
  // print("Authentication tag: ${v.authenticationTag}");
  // // Use the private key to create the decrypter
  // var decrypter = keyPair.privateKey.createEncrypter(algorithms.encryption.aes.gcm);
  // // Decrypt and verify authentication tag
  // var decrypted = decrypter.decrypt(v);
  // print("Decrypted text: '${String.fromCharCodes(decrypted)}'");
}

  jose: ^0.3.4
  cryptography: ^2.5.0
  rsa_encrypt: ^2.0.0
  pointycastle: ^3.7.3

