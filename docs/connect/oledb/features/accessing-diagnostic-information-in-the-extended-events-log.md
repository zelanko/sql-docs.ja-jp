---
title: 拡張イベント ログの診断情報にアクセスする |Microsoft ドキュメント
description: SQL Server の OLE DB ドライバーをトレースして、拡張イベント ログの診断情報にアクセスします。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.openlocfilehash: ea81e8bc007b9afd526901bcd60827238f5356e4
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>拡張イベント ログの診断情報へのアクセス」を参照してください。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  以降で[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、OLE DB Driver for SQL Server とデータ アクセスのトレース ([データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805))、接続リング バッファーからの接続エラーに関する診断情報を取得するが簡単に更新されました拡張イベント ログからアプリケーションのパフォーマンス情報。  
  
 拡張イベント ログの読み取り方法の詳細については、次を参照してください。[イベント セッション データの表示](../../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md)です。 

  
> [!NOTE]  
>  この機能は、トラブルシューティングおよび診断用であるため、監査やセキュリティの用途には適さない場合があります。  
  
## <a name="remarks"></a>解説  
 接続操作では、OLE DB Driver for SQL Server がクライアントに送信接続 id。 接続が失敗した場合、接続リング バッファーにアクセスできます ([、接続リング バッファーによる SQL Server 2008 の接続のトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=207752)) を見つけて、 **ClientConnectionID**フィールドと接続エラーに関する診断情報を取得します。 クライアント接続 ID は、エラーが発生した場合にのみリング バッファーに記録されます  (ログイン前のパケットを送信する前に接続に失敗した場合、クライアント接続 ID は生成されません)。クライアント接続 ID は 16 バイトの GUID です。 クライアントを見つけることもできる場合、拡張イベントの接続 ID は、ターゲットを出力、 **client_connection_id**アクションが拡張イベント セッションのイベントに追加します。 データ アクセスのトレースを有効にして、接続コマンドを再実行し、観察、 **ClientConnectionID** 、失敗した操作のデータ アクセスのトレースでフィールドにはさらに診断サポートが必要な場合です。  
   
  
 OLE DB Driver for SQL Server では、また、スレッド固有のアクティビティ ID を送信します。 アクティビティ ID は、TRACK_CAUSAILITY オプションを有効にしてセッションを開始した場合、拡張イベント セッションでキャプチャされます。 アクティブな接続のパフォーマンス問題については、クライアントのデータ アクセスのトレースからアクティビティ ID を取得することができます (**ActivityID**フィールド) し、拡張イベント出力でアクティビティ ID を見つけます。 拡張イベントのアクティビティ ID は、16 バイトの GUID (クライアント接続 ID の GUID とは異なります) に 4 バイトのシーケンス番号が付加されたものです。 シーケンス番号は、スレッド内の要求の順序を表し、スレッドのバッチ ステートメントと RPC ステートメントの相対順序を示します。 **ActivityID**のデータ アクセスのトレースが有効になり、データ アクセス トレース構成ワードの 18 番目のビットがオンになっているときに必要に応じて SQL バッチ ステートメントと RPC 要求の送信。  
  
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
 SQL Server コントロール ファイル (ctrl.guid) の OLE DB ドライバの内容には。  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x630ff  0   MSDADIAG.ETW
{EE7FB59C-D3E8-9684-AEAC-B214EFD91B31}  0x630ff  0   MSOLEDBSQL.1  
```  
  
## <a name="mof-file"></a>MOF ファイル  
 OLE DB Driver for SQL Server の mof ファイルの内容には。  
  
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
//  MSOLEDBSQL.1  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1"),  
 Guid("{EE7FB59C-D3E8-9684-AEAC-B214EFD91B31}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1"),  
 Guid("{EE7FB59D-D3E8-9684-AEAC-B214EFD91B31}"),  
 DisplayName("MSOLEDBSQL.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace : Bid2Etw_MSOLEDBSQL_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace_TextA : Bid2Etw_MSOLEDBSQL_1_Trace  
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
 Description("MSOLEDBSQL.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace_TextW : Bid2Etw_MSOLEDBSQL_1_Trace  
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
 [エラーの処理](../../oledb/ole-db-errors/errors.md)  
  
  
