---
title: "Always Encrypted で保護された機微なデータの移行 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/04/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Always Encrypted, bulk import
ms.assetid: b2ca08ed-a927-40fb-9059-09496752595e
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 20eb76a9e2cc89015167b5199f1a6f8dd5baec16
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="migrate-sensitive-data-protected-by-always-encrypted"></a>Always Encrypted で保護された機微なデータの移行
 <a name="to-load-encrypted-data-without-performing-metadata-checks-on-the-server-during-bulk-copy-operations-create-the-user-with-the-allowencryptedvaluemodifications-option-this-option-is-intended-to-be-used-by-legacy-tools-from-versions-of-includessnoversionincludesssnoversion-mdmd-older-than-includesssql15includessssql15-mdmd-such-as-bcpexe-or-by-using-third-party-extract-transform-load-etl-work-flows-that-cannot-use-always-encrypted-this-allows-a-user-to-securely-move-encrypted-data-from-one-set-of-tables-containing-encrypted-columns-to-another-set-of-tables-with-encrypted-columns-in-the-same-or-a-different-database"></a>一括コピー操作中にサーバーでメタデータ チェックを実行せずに暗号化されたデータを読み込むには、 **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** オプションを指定してユーザーを作成します。 このオプションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より古いバージョンの [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] から従来のツールで使用するためのものです。Always Encrypted を使用できないサードパーティの ETL (Extract-Transform-Load) ワークフローで使用する場合もあります。 これにより、ユーザーは、暗号化された列を含むあるテーブル セットから、(同じデータベースまたは別のデータベース内の) 暗号化された列を含む別のテーブル セットに暗号化されたデータを安全に移動することができます。  
 -  
 -## ALLOW_ENCRYPTED_VALUE_MODIFICATIONS オプション  
 - [CREATE USER](https://msdn.microsoft.com/library/ms173463.aspx) と [ALTER USER](https://msdn.microsoft.com/library/ms176060.aspx) の両方に ALLOW_ENCRYPTED_VALUE_MODIFICATIONS オプションがあります。 このオプションを ON に設定すると (既定値は OFF)、一括コピー操作でサーバーに対する暗号化メタデータ チェックが抑制されます。これにより、ユーザーはデータの暗号化を解除せずにテーブルまたはデータベース間で暗号化されたデータの一括コピーを行うことができます。  
 -  
 -## データの移行シナリオ  
 - 次の表では、いくつかの移行シナリオに適した推奨設定を示しています。  
 -  
 - ![always-encrypted-migration](../../../relational-databases/security/encryption/media/always-encrypted-migration.PNG "always-encrypted-migration")  
 -  
 -## 暗号化されたデータの一括読み込み  
 - 次のプロセスを使用して、暗号化されたデータを読み込みます。  
 -  
 -1.  一括コピー操作の対象となるデータベース内のユーザーに対して、オプションを ON に設定します。 例:  
 -  
 -    ```  
 -    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON;  
 -    ```  
 -  
 -2.  Run your bulk copy application or tool connecting as that user. (If your application uses an Always Encrypted enabled client driver, make sure the connection string for the data source does not contain **column encryption setting=enabled** to ensure the data retrieved from encrypted columns remains encrypted. For more information, see [Always Encrypted &#40;client development&#41;](../../../relational-databases/security/encryption/always-encrypted-client-development.md).)  
 -  
 -3.  Set the ALLOW_ENCRYPTED_VALUE_MODIFICATIONS option back to OFF. For example:  
 -  
 -    ```  
 -    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = OFF;  
 -    ```  
 -  
 -## Potential for Data Corruption  
 - Improper use of this option can lead to data corruption. The **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** option allows the user to insert any data into encrypted columns in the database, including data that is encrypted with different keys, incorrectly encrypted, or not encrypted at all. If the user accidently copies the data that is not correctly encrypted using the encryption scheme (column encryption key, algorithm, encryption type) set up for the target column, you will not be able to decrypt the data (the data will be corrupted). This option must be used carefully, as it can lead to corrupting data in the database.  
 -  
 - The following scenario demonstrates how improperly importing data could lead to data corruption:  
 -  
 -1.  The option is set to ON for a user.  
 -  
 -2.  The user runs the application that connects to the database. The application uses bulk APIs to insert plain text values to encrypted columns. The application expects an Always Encrypted-enabled client driver to encrypt the data on insert. However, the application is misconfigured, so that either it ends up using a driver that does not support Always Encrypted or the connection string does not contain **column encryption setting=enabled**.  
 -  
 -3.  The application sends plaintext values to the server. As cryptographic metadata checks are disabled in the server for the user, the server lets the incorrect data (plaintext instead of correctly encrypted ciphertext) to be inserted into an encrypted column.  
 -  
 -4.  The same or another application connects to the database using an Always Encrypted-enabled driver and with **column encryption setting=enabled** in the connection string, and retrieves the data. The application expects the data to be transparently decrypted. However, the driver fails to decrypt the data because the data is incorrect ciphertext.  
 -  
 -## Best practice  
 -  
 --   Use designated user accounts for long running workloads using this option.  
 -  
 --   For short running bulk copy applications or tools that need to move encrypted data without decrypting it, set the option to ON immediately before running the application and set it back to OFF immediately after running the operation.  
 -  
 --   Do not use this option for developing new applications. Instead, use a client driver (such as  ADO 4.6.1) that offers an API for suppressing cryptographic metadata checks for a single session.  
 -  
 -## See Also  
 - [CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md)   
 - [ALTER USER &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-user-transact-sql.md)   
 - [Always Encrypted &#40;Database Engine&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 - [Always Encrypted Wizard](../../../relational-databases/security/encryption/always-encrypted-wizard.md)   
 - [Always Encrypted &#40;client development&#41;](../../../relational-databases/security/encryption/always-encrypted-client-development.md)  
