---
title: "DataFactory オブジェクト (RDSServer) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 24068333604b7ab6edea96567a4c0410d0df808a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="datafactory-object-rdsserver"></a>DataFactory オブジェクト (RDSServer)
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 この既定のサーバー側のビジネス オブジェクトでは、クライアント側アプリケーションの指定されたデータ ソースへの読み取り/書き込みデータのアクセスを提供するメソッドを実装します。  
  
 **RDSServer.DataFactory**オブジェクトがクライアント要求を受信するサーバー側のオートメーション オブジェクトとして設計されています。 実装では、インターネット、Web サーバー上に常駐し、ADISAPI コンポーネントによってインスタンス化します。 **RDSServer.DataFactory**オブジェクトは読み取りを提供し、指定されたデータへの書き込みアクセスは、ソースが、検証やビジネス ルールのロジックが含まれていません。  
  
 両方で使用可能なメソッドを使用する場合、 **RDSServer.DataFactory**と[.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトをリモートのデータ サービスを使用して、 **.rds ですDataControl**既定のバージョン。 既定値は基本的なプログラミング シナリオでは、場所、 **RDSServer.DataFactory**汎用的なサーバー側のビジネス オブジェクトとして機能します。  
  
 置き換えることができます、Web アプリケーション タスクに固有のサーバー側の処理を処理する場合は、 **RDSServer.DataFactory**カスタム ビジネス オブジェクトを使用します。  
  
 呼び出すサーバー側のビジネス オブジェクトを作成することができます、 **RDSServer.DataFactory**メソッドなど[クエリ](../../../ado/reference/rds-api/query-method-rds.md)と[CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)です。 これは、ビジネス オブジェクトに機能を追加、既存のリモート データ サービス テクノロジを利用する場合に便利です。  
  
 **DataFactory**オブジェクトは、クライアント側で実行されるスクリプトに対して安全ではありません。  
  
 クラス ID、 **RDSServer.DataFactory**オブジェクトが 9381D8F5 0288 11 D 0-9501-00AA00B911A5 です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [DataFactory オブジェクト (RDSServer) のプロパティ、メソッド、およびイベント](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [DataFactory オブジェクト、クエリのメソッド、および CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)



