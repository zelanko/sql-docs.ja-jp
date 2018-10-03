---
title: DataFactory オブジェクト (RDSServer) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 512174e0a5e8e593dcfbd075d5f459cb2d92d8c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602770"
---
# <a name="datafactory-object-rdsserver"></a>DataFactory オブジェクト (RDSServer)
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
 この既定のサーバー側ビジネス オブジェクトは、クライアント側のアプリケーションの指定したデータ ソースへの読み取り/書き込みデータのアクセスを提供するメソッドを実装します。  
  
 **RDSServer.DataFactory**オブジェクトがクライアント要求を受信するサーバー側のオートメーション オブジェクトとして設計されています。 インターネット実装では、Web サーバー上に存在し、ADISAPI コンポーネントによりインスタンス化されます。 **RDSServer.DataFactory**オブジェクトは読み取りを提供し、指定されたデータへの書き込みアクセスが、ソースしますが、検証やビジネス ルールのロジックが含まれていません。  
  
 両方で使用できるメソッドを使用する場合、 **RDSServer.DataFactory**と[rds.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの場合、リモート データ サービスを使用して、 **rds.DataControl**既定のバージョン。 既定の基本的なプログラミング シナリオでは、前提としています、 **RDSServer.DataFactory**汎用的なサーバー側ビジネス オブジェクトとして機能します。  
  
 タスク固有のサーバー側の処理を処理するために、Web アプリケーションを実行する場合に、置き換えることができます、 **RDSServer.DataFactory**カスタム ビジネス オブジェクトを使用します。  
  
 呼び出すサーバー側ビジネス オブジェクトを作成することができます、 **RDSServer.DataFactory**メソッドなど[クエリ](../../../ado/reference/rds-api/query-method-rds.md)と[CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)します。 これは、ビジネス オブジェクトに機能を追加、既存のリモート データ サービス テクノロジを活用する場合に役立ちます。  
  
 **DataFactory**オブジェクトは、クライアント側で実行されるスクリプトに対して安全ではありません。  
  
 クラス ID を**RDSServer.DataFactory**オブジェクトが 9381D8F5-0288-11 D 0-9501-00AA00B911A5 します。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [DataControl オブジェクト (RDSServer) のプロパティ、メソッド、およびイベント](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [DataFactory オブジェクト、クエリ メソッド、および CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


