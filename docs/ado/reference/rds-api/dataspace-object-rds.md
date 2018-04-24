---
title: DataSpace オブジェクト (RDS) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace object [RDS]
ms.assetid: 9194bffa-5bdf-4dff-af86-f7158c23bfa7
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4fadcb31a6978cf383e3e432d48279964099de2d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="dataspace-object-rds"></a>DataSpace オブジェクト (RDS)
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 中間層に配置されているカスタム ビジネス オブジェクトにクライアント側プロキシを作成します。  
  
 リモート データ サービスでは、クライアント側のコンポーネントは、中間層にあるビジネス オブジェクトと通信できるようにするビジネス オブジェクトのプロキシが必要です。 パッケージ化、アンパッケージ処理、およびトランスポート (マーシャ リング) アプリケーションのプロキシが容易に[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)プロセスやコンピューターの境界を越えてデータ。  
  
 リモート データ サービスを使用して、 **.rds ですDataSpace**オブジェクトの[CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md)ビジネス オブジェクトのプロキシを作成します。 中間層のビジネス オブジェクトの対応のインスタンスが作成されるたびに、ビジネス オブジェクトのプロキシが動的に作成します。 リモート データ サービスは、次のプロトコルをサポートしています: HTTP、HTTPS (HTTP Secure Sockets)、DCOM、およびインプロセス (クライアント コンポーネントと同じコンピューターに存在しているビジネス オブジェクト)。  
  
> [!NOTE]
>  RDS の"ステートレスな"方法で動作時に、 **.rds ですDataSpace**オブジェクトは、HTTP または HTTPS プロトコルを使用します。 つまり、サーバーの応答が返された後、クライアントの要求に関する内部情報は破棄されます。  
  
> [!NOTE]
>  ビジネス オブジェクトは、ビジネス オブジェクトのプロキシの有効期間の存在に見えますが、ビジネス オブジェクトは、要求に応答が送信されるまでの間だけに実際に存在します。 要求が発行されたとき (つまり、メソッドを呼び出すと、ビジネス オブジェクトに)、プロキシ サーバーへの新しい接続が開き、サーバーは、ビジネス オブジェクトの新しいインスタンスを作成します。 ビジネス オブジェクトは、要求に応答して、サーバーがビジネス オブジェクトを破棄して、接続を閉じます。  
  
> [!NOTE]
>  この動作は、ビジネス オブジェクトのプロパティまたは変数を使用して、1 つの要求からデータを渡すことはできませんを意味します。 ファイルまたは状態データを保持する、メソッドの引数など、他のいくつかのメカニズムを使用する必要があります。  
  
 クラス ID、 **.rds ですDataSpace**オブジェクトが BD96C556 65A3-11-d 0 983A 00C04FC29E36 です。  
  
 **DataSpace**オブジェクトにスクリプトを実行しても安全です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [DataSpace オブジェクト (RDS) のプロパティ、メソッド、およびイベント](../../../ado/reference/rds-api/dataspace-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [DataSpace オブジェクトおよび CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)


