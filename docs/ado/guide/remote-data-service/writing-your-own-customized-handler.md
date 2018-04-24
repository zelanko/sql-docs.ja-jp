---
title: 独自のカスタム ハンドラーの記述 |Microsoft ドキュメント
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
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
- customized handler in RDS [ADO]
ms.assetid: d447712a-e123-47b5-a3a4-5d366cfe8d72
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2aebf16b3fea3933b1ef9b565b7f76b17d8c2b71
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="writing-your-own-customized-handler"></a>独自のカスタム ハンドラーの記述
RDS をサポートして、既定値を希望する IIS サーバー管理者がいるかどうか、独自のハンドラーを記述することがありますが、ユーザーの要求制御の強化とアクセス権。  
  
 MSDFMAP です。ハンドラーを実装して、 **IDataFactoryHandler**インターフェイスです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="idatafactoryhandler-interface"></a>IDataFactoryHandler インターフェイス  
 このインターフェイスは 2 つのメソッド、 **GetRecordset**と**再接続**です。 どちらの方法を必要とする、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定する**adUseClient**です。  
  
 どちらの方法は、最初のコンマの後に指定した引数を受け取る、"**ハンドラー =**"キーワード。 たとえば、`"Handler=progid,arg1,arg2;"`の引数の文字列を渡す`"arg1,arg2"`、および`"Handler=progid"`null 引数を渡します。  
  
## <a name="getrecordset-method"></a>GetRecordset メソッド  
 このメソッドは、データ ソースを照会し、新たに作成[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト指定された引数を使用します。 **Recordset**で開く必要がある**adLockBatchOptimistic**され、非同期的に開かれません必要があります。  
  
### <a name="arguments"></a>引数  
 ***conn***接続文字列。  
  
 ***args***ハンドラーの引数。  
  
 ***クエリ***コマンド テキストをクエリを作成します。  
  
 ***ppRS***ポインターを**Recordset**返される必要があります。  
  
## <a name="reconnect-method"></a>メソッドを再接続します。  
 このメソッドは、データ ソースを更新します。 新しいを作成[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトとの接続、指定された**Recordset**です。  
  
### <a name="arguments"></a>引数  
 ***conn***接続文字列。  
  
 ***args***ハンドラーの引数。  
  
 ***Pr*** A **Recordset**オブジェクト。  
  
## <a name="msdfhdlidl"></a>msdfhdl.idl  
 これは、インターフェイス定義**IDataFactoryHandler**に表示される、 **msdfhdl.idl**ファイル。  
  
```  
[  
  uuid(D80DE8B3-0001-11d1-91E6-00C04FBBBFB3),  
  version(1.0)  
]  
library MSDFHDL  
{  
    importlib("stdole32.tlb");  
    importlib("stdole2.tlb");  
  
    // TLib : Microsoft ActiveX Data Objects 2.0 Library  
    // {00000200-0000-0010-8000-00AA006D2EA4}  
    #ifdef IMPLIB  
    importlib("implib\\x86\\release\\ado\\msado15.dll");  
    #else  
    importlib("msado20.dll");  
    #endif  
  
    [  
      odl,  
      uuid(D80DE8B5-0001-11d1-91E6-00C04FBBBFB3),  
      version(1.0)  
    ]  
    interface IDataFactoryHandler : IUnknown  
    {  
HRESULT _stdcall GetRecordset(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] BSTR query,  
      [out, retval] _Recordset **ppRS);  
  
// DataFactory will use the ActiveConnection property  
// on the Recordset after calling Reconnect.  
   HRESULT _stdcall Reconnect(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] _Recordset *pRS);  
    };  
};  
```  
  
## <a name="see-also"></a>参照  
 [カスタマイズ ファイルのセクションを接続します。](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズ ファイル ログ](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [カスタマイズ ファイル SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [カスタマイズ ファイル UserList に関するセクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)


