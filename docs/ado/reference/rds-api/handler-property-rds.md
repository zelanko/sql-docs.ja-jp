---
title: "ハンドラーのプロパティ (RDS) |Microsoft ドキュメント"
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
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 25ac7c676fbab1e8b5899a3502fab2199b0afd22
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="handler-property-rds"></a>ハンドラーのプロパティ (RDS)
機能を拡張するプログラム (ハンドラー) のサーバー側のカスタマイズの名前を示す、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)とで使用される任意のパラメーター、*ハンドラー*です。  
  
 **適用対象:** [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *文字列*  
 A**文字列**コンマで区切ってすべてハンドラーと、パラメーターの名前を表す値 (たとえば、 `"handlerName,parm1,parm2,...,parm` *N*`"`)。  
  
## <a name="remarks"></a>解説  
 このプロパティをサポートしている[カスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)、設定を必要とする機能を使用する、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**です。  
  
 ハンドラーは、し、そのパラメーターの名前は、存在する場合、コンマで区切られます (「,」) です。 予期しない動作が発生、セミコロン (「;」) 内で任意の場所が表示されます。*文字列*です。 独自のハンドラーを記述するには、サポート提供、 **IDataFactoryHandler**インターフェイスです。  
  
 既定のハンドラーの名前は**MSDFMAP です。ハンドラー**、その既定のパラメーターは、という名前のカスタマイズ ファイルおよび**MSDFMAP です。INI**です。 このプロパティを使用して、サーバー管理者によって作成される代替のカスタマイズ ファイルを呼び出します。  
  
 設定する代わりに、**ハンドラー**プロパティがハンドラーと内のパラメーターを指定するには、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティですつまり、"**ハンドラー =**  *。handlerName、parameter1、parameter2、います。*".  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ハンドラー プロパティの例 (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)



