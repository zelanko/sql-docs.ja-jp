---
title: Handler プロパティ (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a7423879b8263d87575d913c4863143faf3573e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964007"
---
# <a name="handler-property-rds"></a>Handler プロパティ (RDS)
[RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)の機能を拡張するサーバー側のカスタマイズプログラム (ハンドラー) の名前と、*ハンドラー*によって使用されるすべてのパラメーターを示します。  
  
 **適用対象:** [DATACONTROL オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 RDS を表すオブジェクト変数です[。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *String*  
 ハンドラーの名前とすべてのパラメーターをコンマで区切って指定した**文字列**値 ( `"handlerName,parm1,parm2,...,parm` *N*`"`など)。  
  
## <a name="remarks"></a>解説  
 このプロパティは、[[カーソルの場所](../../../ado/reference/ado-api/cursorlocation-property-ado.md)] プロパティを**adUseClient**に設定する必要がある機能である[カスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)をサポートします。  
  
 ハンドラーの名前とそのパラメーター (存在する場合) は、コンマ (",") で区切られます。 *文字列*内の任意の場所にセミコロン (";") がある場合、予期しない動作が発生します。 **IDataFactoryHandler**インターフェイスがサポートされていれば、独自のハンドラーを作成できます。  
  
 既定のハンドラーの名前は**Msdfmap です。ハンドラー**とその既定のパラメーターは、Msdfmap という名前のカスタマイズファイルです **。INI**。 このプロパティを使用して、サーバー管理者によって作成された代替のカスタマイズファイルを呼び出します。  
  
 **ハンドラー**プロパティを設定する代わりに、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティでハンドラーとパラメーターを指定することもできます。つまり、"**Handler =**_handlername, parameter1, parameter2,...;_" となります。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [Handler プロパティの例 (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


