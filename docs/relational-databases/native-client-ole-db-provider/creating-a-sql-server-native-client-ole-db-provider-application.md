---
title: SQL Server Native Client OLE DB プロバイダー アプリケーションの作成 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a72ec9a619294468a024049b1a32b0a56508c094
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085852"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>SQL Server Native Client OLE DB プロバイダー アプリケーションの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  作成、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー アプリケーションがこれらの手順が含まれます。  
  
1.  データ ソースへの接続の確立。  
  
2.  コマンドの実行。  
  
3.  結果を処理します。  
  
> [!NOTE]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保存する必要がある場合は、[Win32 CryptoAPI](http://go.microsoft.com/fwlink/?LinkId=9504) を使用して暗号化してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ソースへの接続の確立](../../relational-databases/native-client-ole-db-provider/establishing-a-connection-to-a-data-source.md)  
  
-   [コマンドの実行](../../relational-databases/native-client-ole-db-provider/executing-a-command.md)  
  
-   [結果の処理](../../relational-databases/native-client-ole-db-provider/processing-results.md)  
  
-   [OLE DB プロパティについて](../../relational-databases/native-client-ole-db-provider/about-ole-db-properties.md)  
  
-   [SQL Server Native Client の OLE DB での OUTPUT 句の使用](../../relational-databases/native-client-ole-db-provider/using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
