---
title: "CreateObject メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aeca3cd5d525a3712511a3d7fd59f82210c041e0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="createobject-method-rds"></a>CreateObject メソッド (RDS)
対象のビジネス オブジェクトのプロキシを作成し、ポインターを返します。 インターネット経由で要求とデータを送信するビジネス オブジェクトとの通信のサーバー側のスタブをプロキシ パッケージとマーシャ リング データ。 インプロセス コンポーネント オブジェクトのプロキシは使用されず、オブジェクトへのポインターのみが提供されます。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
 リモート データ サービスは、次のプロトコルをサポートしています: HTTP、HTTPS (HTTP over Secure Socket Layer)、DCOM、および処理中です。  
  
|[プロトコル]|構文|  
|--------------|------------|  
|HTTP|Set object = DataSpace.CreateObject("ProgId", "http://awebsrvr")|  
|HTTPS|Set object = DataSpace.CreateObject("ProgId", "https://awebsrvr")|  
|DCOM|Set object = DataSpace.CreateObject("ProgId", "computername")|  
|インプロセス|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>パラメーター  
 *オブジェクト*  
 オブジェクト変数で指定された型であるオブジェクトに評価される*ProgID*です。  
  
 *DataSpace*  
 オブジェクト変数を表す、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクトが、新しいオブジェクトのインスタンスを作成するために使用します。  
  
 *ProgID*  
 A**文字列**プログラムに、アプリケーションのビジネス ルールを実装しているサーバー側のビジネス オブジェクトを指定する識別子を含む値です。  
  
 *awebsrvr*または*computername*  
 A**文字列**サーバー ビジネス オブジェクトのインスタンスが作成されたインターネット インフォメーション サービス (IIS) Web サーバーを識別する URL を表す値です。  
  
## <a name="remarks"></a>解説  
 *HTTP プロトコル*標準的な Web プロトコルです。*HTTPS*は安全な Web プロトコルです。 使用して、 *DCOM プロトコル*HTTP を使用しないローカル エリア ネットワークを実行する場合。 *インプロセス*プロトコルは、ローカルのダイナミック リンク ライブラリ (DLL) ですが、ネットワークは使用されません。  
  
## <a name="applies-to"></a>適用対象  
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [DataFactory オブジェクト、クエリのメソッド、および CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [DataSpace オブジェクトおよび CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [CreateRecordset メソッド (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


