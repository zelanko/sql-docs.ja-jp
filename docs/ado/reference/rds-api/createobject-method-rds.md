---
title: CreateObject メソッド (RDS) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0307edbf2e9b5a6495dd84c45c8dc647fe5bdefd
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35287571"
---
# <a name="createobject-method-rds"></a>CreateObject メソッド (RDS)
対象のビジネス オブジェクトのプロキシを作成し、ポインターを返します。 インターネット経由で要求とデータを送信するビジネス オブジェクトとの通信のサーバー側のスタブをプロキシ パッケージとマーシャ リング データ。 インプロセス コンポーネント オブジェクトのプロキシは使用されず、オブジェクトへのポインターのみが提供されます。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
 リモート データ サービスは、次のプロトコルをサポートしています: HTTP、HTTPS (HTTP over Secure Socket Layer)、DCOM、および処理中です。  
  
|[プロトコル]|構文|  
|--------------|------------|  
|HTTP|Set オブジェクト = DataSpace.CreateObject ("ProgId"、"http://awebsrvr")|  
|HTTPS|Set オブジェクト = DataSpace.CreateObject ("ProgId"、"https://awebsrvr")|  
|DCOM|Set オブジェクト DataSpace.CreateObject ("ProgId"、"computername") を =|  
|インプロセス|Set オブジェクト = DataSpace.CreateObject ("ProgId"、"")|  
  
## <a name="parameters"></a>パラメーター  
 *Object*  
 オブジェクト変数で指定された型であるオブジェクトに評価される*ProgID*です。  
  
 *DataSpace*  
 オブジェクト変数を表す、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクトが、新しいオブジェクトのインスタンスを作成するために使用します。  
  
 *ProgID*  
 A**文字列**プログラムに、アプリケーションのビジネス ルールを実装しているサーバー側のビジネス オブジェクトを指定する識別子を含む値です。  
  
 *awebsrvr*または*computername*  
 A**文字列**サーバー ビジネス オブジェクトのインスタンスが作成されたインターネット インフォメーション サービス (IIS) Web サーバーを識別する URL を表す値です。  
  
## <a name="remarks"></a>コメント  
 *HTTP プロトコル*標準的な Web プロトコルです。*HTTPS*は安全な Web プロトコルです。 使用して、 *DCOM プロトコル*HTTP を使用しないローカル エリア ネットワークを実行する場合。 *インプロセス*プロトコルは、ローカルのダイナミック リンク ライブラリ (DLL) ですが、ネットワークは使用されません。  
  
## <a name="applies-to"></a>適用対象  
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [DataFactory オブジェクト、クエリのメソッド、および CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [DataSpace オブジェクトおよび CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [CreateRecordset メソッド (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


