---
title: 拡張イベント ログの診断情報へのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: aaa180c2-5e1a-4534-a125-507c647186ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 902110d601b9ea4b68fb04e8fb91e66400a452e9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049611"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>拡張イベント ログの診断情報へのアクセス
  以降で [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client とデータアクセスのトレース ([データアクセスのトレース](https://go.microsoft.com/fwlink/?LinkId=125805)) が更新され、接続リングバッファーおよび拡張イベントログからのアプリケーションのパフォーマンス情報からの接続エラーに関する診断情報を簡単に取得できるようになりました。  
  
 拡張イベント ログを表示する方法については、「[イベント セッション データの表示](../../../database-engine/view-event-session-data.md)」を参照してください。  
  
> [!NOTE]  
>  この機能は、トラブルシューティングおよび診断用であるため、監査やセキュリティの用途には適さない場合があります。  
  
## <a name="remarks"></a>Remarks  
 接続操作では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はクライアント接続 ID を送信します。 接続に失敗した場合は、接続リング バッファー ([接続リング バッファーによる SQL Server 2008 での接続トラブルシューティング](https://go.microsoft.com/fwlink/?LinkId=207752)に関する記事を参照) にアクセスし、`ClientConnectionID` フィールドを見つけて、接続エラーに関する診断情報を取得することができます。 クライアント接続 ID は、エラーが発生した場合にのみリング バッファーに記録されます (ログイン前のパケットを送信する前に接続に失敗した場合、クライアント接続 ID は生成されません。)クライアント接続 ID は 16 バイトの GUID です。 拡張イベント `client_connection_id` セッションのイベントにアクションが追加されている場合は、拡張イベントの出力ターゲットでクライアント接続 ID を検索することもできます。 詳しい診断サポートが必要な場合は、データ アクセスのトレースを有効にして、接続コマンドを再実行し、失敗した操作のデータ アクセスのトレースで `ClientConnectionID` フィールドを調べます。  
  
 Native Client で ODBC を使用していて、接続に成功した場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `SQL_COPT_SS_CLIENT_CONNECTION_ID` [Sqlgetconnectattr](../../native-client-odbc-api/sqlgetconnectattr.md)属性を使用して、クライアント接続 ID を取得できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、スレッド固有のアクティビティ ID も送信します。 アクティビティ ID は、TRACK_CAUSAILITY オプションを有効にしてセッションを開始した場合、拡張イベント セッションでキャプチャされます。 アクティブな接続のパフォーマンスの問題については、クライアントのデータ アクセスのトレース (`ActivityID` フィールド) からアクティビティ ID を取得した後、その拡張イベントの出力のアクティビティ ID を検索できます。 拡張イベントのアクティビティ ID は、16 バイトの GUID (クライアント接続 ID の GUID とは異なります) に 4 バイトのシーケンス番号が付加されたものです。 シーケンス番号は、スレッド内で要求の順序を表し、スレッドのバッチと RPC ステートメントの相対的順序を示します。 `ActivityID` は必要に応じて、データ アクセスのトレースが有効であり、データ アクセス トレース構成ワードの 18 番目のビットがオンである場合に、SQL バッチ ステートメントと RPC 要求に送信されます。  
  
 次のサンプルでは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して拡張イベント セッションを開始します。このセッションは、リング バッファーに保存され、RPC およびバッチ操作でクライアントから送信されたアクティビティ ID を記録します。  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a>制御ファイル  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の SQL Server Native Client 制御ファイル (ctrl.guid.snac11) の内容は次のとおりです。  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x00000000  0   MSDADIAG.ETW  
{2DA81B52-908E-7DB6-EF81-76856BB47C4F}  0xFFFFFFFF  0   SQLNCLI11.1  
```  
  
## <a name="mof-file"></a>MOF ファイル  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の SQL Server Native Client MOF ファイルの内容は次のとおりです。  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  SQLNCLI11.1  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B52-908E-7DB6-EF81-76856BB47C4F}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B53-908E-7DB6-EF81-76856BB47C4F}"),  
 DisplayName("SQLNCLI11.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace : Bid2Etw_SQLNCLI11_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextA : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextW : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
