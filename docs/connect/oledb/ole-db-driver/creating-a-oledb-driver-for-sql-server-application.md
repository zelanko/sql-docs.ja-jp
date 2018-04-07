---
title: SQL Server アプリケーションの OLE DB ドライバーの作成 |Microsoft ドキュメント
description: OLE DB Driver for SQL Server アプリケーションを作成します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bbd9dafbd44b83d5e33c41980ca4c4fb9dc63e0e
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>SQL Server アプリケーション用の OLE DB ドライバーを作成します。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server アプリケーションを作成するには、次の手順が含まれます。  
  
1.  データ ソースへの接続を確立します。  
  
2.  コマンドを実行します。  
  
3.  結果を処理します。  
  
> [!NOTE]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合、それらを暗号化する必要があります[Win32 cryptoAPI](http://go.microsoft.com/fwlink/?LinkId=9504)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ソースへの接続を確立します。](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [コマンドの実行](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [結果の処理](../../oledb/ole-db-driver/processing-results.md)  
  
-   [OLE DB プロパティについて](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [OLE DB Driver for SQL Server での OLE DB を使用した OUTPUT 句の使用](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
