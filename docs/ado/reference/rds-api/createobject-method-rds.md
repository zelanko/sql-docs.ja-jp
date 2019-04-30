---
title: CreateObject メソッド (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d220a9abc0e2dc72d7ab65306b514a9925b4fc43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281056"
---
# <a name="createobject-method-rds"></a>CreateObject メソッド (RDS)
対象のビジネス オブジェクトのプロキシを作成し、ポインターを返します。 サーバー側のスタブ、インターネット経由で要求とデータを送信するビジネス オブジェクトとの通信をプロキシ パッケージとマーシャ リング データ。 インプロセス コンポーネントのオブジェクトのプロキシは使用されず、オブジェクトへのポインターのみが提供されます。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="syntax"></a>構文  
 リモート データ サービスには、次のプロトコルがサポートされています。HTTP、HTTPS (HTTP over Secure Socket Layer)、DCOM、およびプロセスにします。  
  
|プロトコル|構文|  
|--------------|------------|  
|HTTP|Set object = DataSpace.CreateObject("ProgId", "https\://awebsrvr")|  
|HTTPS|Set object = DataSpace.CreateObject("ProgId", "https\://awebsrvr")|  
|DCOM|Set オブジェクト DataSpace.CreateObject ("ProgId"、"computername") を =|  
|インプロセス|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>パラメーター  
 *Object*  
 オブジェクト変数で指定された型のオブジェクトに評価される*ProgID*します。  
  
 *DataSpace*  
 オブジェクト変数を表す、 [rds.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクトの新しいオブジェクトのインスタンスを作成するために使用します。  
  
 *ProgID*  
 A**文字列**プログラムに、アプリケーションのビジネス ルールを実装するサーバー側ビジネス オブジェクトを指定する識別子を表す値です。  
  
 *awebsrvr*または*computername*  
 A**文字列**server のビジネス オブジェクトのインスタンスが作成される場所、インターネット インフォメーション サービス (IIS) Web サーバーを識別する URL を表す値です。  
  
## <a name="remarks"></a>コメント  
 *HTTP プロトコル*標準的な Web プロトコルです。*HTTPS*はセキュリティで保護された Web プロトコルです。 使用して、 *DCOM プロトコル*HTTP を使用しないローカル エリア ネットワークを実行する場合。 *インプロセス*プロトコルは、ローカルのダイナミック リンク ライブラリ (DLL) は、ネットワークを使用しません。  
  
## <a name="applies-to"></a>適用対象  
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [DataFactory オブジェクト、クエリ メソッドをおよび CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [DataSpace オブジェクトおよび CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [CreateRecordset メソッド (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


