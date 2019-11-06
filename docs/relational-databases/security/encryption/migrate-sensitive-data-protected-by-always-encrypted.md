---
title: Always Encrypted で保護された機微なデータの移行 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, bulk import
ms.assetid: b2ca08ed-a927-40fb-9059-09496752595e
author: aliceku
ms.author: aliceku
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ff72a94df79c6f8fe7b8bb37caeb57587e44b034
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111671"
---
# <a name="migrate-sensitive-data-protected-by-always-encrypted"></a>Always Encrypted で保護された機微なデータの移行
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

一括コピー操作中にサーバーでメタデータ チェックを実行せずに暗号化されたデータを読み込むには、 **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** オプションを指定してユーザーを作成します。 このオプションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より古いバージョンの [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] から従来のツールで使用するためのものです。Always Encrypted を使用できないサードパーティの ETL (Extract-Transform-Load) ワークフローで使用する場合もあります。 これにより、ユーザーは、暗号化された列を含むあるテーブル セットから、(同じデータベースまたは別のデータベース内の) 暗号化された列を含む別のテーブル セットに暗号化されたデータを安全に移動することができます。  

 ## <a name="the-allowencryptedvaluemodifications-option"></a>ALLOW_ENCRYPTED_VALUE_MODIFICATIONS オプション  
 [CREATE USER](../../../t-sql/statements/create-user-transact-sql.md) と [ALTER USER](../../../t-sql/statements/alter-user-transact-sql.md) の両方に ALLOW_ENCRYPTED_VALUE_MODIFICATIONS オプションがあります。 このオプションを ON に設定すると (既定値は OFF)、一括コピー操作でサーバーに対する暗号化メタデータ チェックが抑制されます。これにより、ユーザーはデータの暗号化を解除せずにテーブルまたはデータベース間で暗号化されたデータの一括コピーを行うことができます。  
  
## <a name="data-migration-scenarios"></a>データの移行シナリオ  
次の表では、いくつかの移行シナリオに適した推奨設定を示しています。  
 
![always-encrypted-migration](../../../relational-databases/security/encryption/media/always-encrypted-migration.PNG "always-encrypted-migration")  

## <a name="bulk-loading-of-encrypted-data"></a>暗号化されたデータの一括読み込み  
次のプロセスを使用して、暗号化されたデータを読み込みます。  

1.  一括コピー操作の対象となるデータベース内のユーザーに対して、オプションを ON に設定します。 例:  
 
   ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON;  
   ```  

2.  そのユーザーとして接続して、一括コピー アプリケーションまたはツールを実行します。 (アプリケーションで Always Encrypted が有効なクライアント ドライバーを使用する場合は、暗号化された列から取得されたデータが暗号化された状態のままになるように、データ ソースの接続文字列に **column encryption setting=enabled** が含まれていないことを確認します。 詳細については、「 [Always Encrypted &#40;クライアント開発&#41;](../../../relational-databases/security/encryption/always-encrypted-client-development.md)」(Always Encrypted &amp;#40;クライアント開発&amp;#41;) を参照してください。  
  
3.  ALLOW_ENCRYPTED_VALUE_MODIFICATIONS オプションを OFF に戻します。 例:  

    ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = OFF;  
    ```  

## <a name="potential-for-data-corruption"></a>データ破損の可能性  
このオプションを不適切に使用すると、データが破損する場合があります。 **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** オプションでは、ユーザーはデータベース内の暗号化された列に任意のデータを挿入することができます。これには、さまざまなキーで暗号化されたデータ、適切に暗号化されていないか、まったく暗号化されていないデータが含まれます。 ユーザーが、対象列に設定されている暗号化スキーム (列暗号化キー、アルゴリズム、暗号化の種類) を使用して適切に暗号化されていないデータを誤ってコピーした場合、データの暗号化を解除することはできません (データが破損します)。 このオプションは、データベース内のデータが破損する場合があるため、慎重に使用する必要があります。  

次のシナリオでは、データが破損する可能性のあるデータの不適切なインポートについて説明します。  

1.  あるユーザーに対して、オプションを ON に設定します。  
 
2.  このユーザーは、データベースに接続されているアプリケーションを実行します。 アプリケーションは一括 API を使用して、暗号化された列にプレーン テキスト値を挿入します。 アプリケーションには、挿入時にデータを暗号化するために Always Encrypted が有効なクライアント ドライバーが必要です。 しかし、アプリケーションが正しく構成されていないため、結局、Always Encrypted をサポートしていないドライバー、または **column encryption setting=enabled**が含まれていない接続文字列が使用されます。  

3.  アプリケーションはプレーンテキスト値をサーバーに送信します。 暗号化メタデータ チェックがユーザーのサーバーでは無効になっているため、サーバーでは不適切なデータ (適切に暗号化された暗号化テキストではなくプレーンテキスト) を暗号化された列に挿入することができます。  
 
4.  同じアプリケーションまたは別のアプリケーションは、Always Encrypted が有効なドライバーを使用し、接続文字列で **column encryption setting=enabled** を指定してデータベースに接続し、データを取得します。 アプリケーションは、透過的にデータの暗号化が解除されることを期待します。 しかし、データが不適切な暗号化テキストであるため、ドライバーはデータの暗号化を解除できません。  

## <a name="best-practice"></a>ベスト プラクティス  
 
長時間実行のワークロードの場合は、このオプションを使用して指定されたユーザー アカウントを使用します。  
 
暗号化されたデータの暗号化を解除せずに移動する必要がある、短時間実行の一括コピー アプリケーションまたはツールの場合は、アプリケーションを実行する直前にオプションを ON に設定し、操作の実行直後に OFF に戻します。  
 
新しいアプリケーションの開発には、このオプションを使用しないでください。 代わりに、クライアント ドライバー (ADO 4.6.1 など) を使用してください。このドライバーでは、1 つのセッションの暗号化メタデータ チェックを抑制するための API が提供されます。  

## <a name="see-also"></a>参照  
[CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md)   
[ALTER USER &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-user-transact-sql.md)   
[Always Encrypted &#40;データベース エンジン&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
[Always Encrypted ウイザード](../../../relational-databases/security/encryption/always-encrypted-wizard.md)   
[Always Encrypted &#40;クライアント開発&#41;](../../../relational-databases/security/encryption/always-encrypted-client-development.md)  
