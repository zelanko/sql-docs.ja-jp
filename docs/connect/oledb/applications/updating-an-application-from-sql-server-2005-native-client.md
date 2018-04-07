---
title: SQL Server 2005 Native Client からのアプリケーションの更新 |Microsoft ドキュメント
description: SQL Server 2005 Native Client からのアプリケーションの更新
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e583abd0a5d84d4842a441fcb8093bbfcf6b9b26
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>SQL Server 2005 Native Client からのアプリケーションの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  以降の SQL Server の OLE DB ドライバーの重要な変更について説明[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client に[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。  

 Microsoft Data Access Components (MDAC) を OLE DB Driver for SQL Server にアップグレードするときに、その動作の違いも表示があります。 詳細については、次を参照してください。 [MDAC から SQL Server の OLE DB Driver をアプリケーションの更新](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)です。  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 が付属[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 が付属[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]です。  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に付属する [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 10.5。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] および [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] に付属する [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client 11.0。  

|比較すると、SQL Server の OLE DB ドライバーの動作が変更されて[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]Native Client|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB によって定義された有効桁数までしか埋め込まれない|OLE DB Driver for SQL Server、サーバーへの変換後のデータの送信先の変換をデータの最大長までしかに後続のゼロが埋め込まれます**datetime**値。 SQL Server Native Client 9.0 では、9 桁まで埋め込まれていました。|  
|ICommandWithParameter::SetParameterInfo DBTYPE_DBTIMESTAMP を検証します。|OLE DB Driver for SQL Server には、OLE DB 要件が実装され*bScale* DBTYPE_DBTIMESTAMP の秒の小数部の有効桁数を設定する ICommandWithParameter::SetParameterInfo にします。|  
|**Sp_columns**ストアド プロシージャを今すぐ返します**"NO"**の代わりに**"NO"**によって IS_NULLABLE 列にします。|OLE DB Driver for SQL Server で**sp_columns**ストアド プロシージャを今すぐ返します**"NO"**の代わりに**"NO"**によって IS_NULLABLE 列です。|  
|Sqlsetdescrec による、SQLBindCol、SQLBindParameter、一貫性チェックが実行されます。|前のバージョン[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]SQLSetDescRec、SQLBindParameter、または SQLBindCol 記述子の型に対して整合性チェックが Native Client 10.0、SQL_DESC_DATA_PTR を設定では発生しませんでした。|  
|SQLCopyDesc が、記述子の一貫性をチェックします。|前のバージョン[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 10.0 SQLCopyDesc しなかった、整合性チェック、SQL_DESC_DATA_PTR フィールドが特定のレコードで設定されたときにします。|  
|SQLGetDescRec 不要になったは記述子の一貫性を確認します。|前のバージョン[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 10.0 SQLGetDescRec 実行記述子の一貫性チェック、SQL_DESC_DATA_PTR フィールドが設定されたときにします。 この一貫性チェックは、ODBC 仕様では不要になったため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) 以降のバージョンでは行われなくなりました。|  
|日付が範囲外の場合に別のエラーが返される|**Datetime**タイプ、別のエラー番号によって返される OLE DB Driver for SQL Server の範囲外の日付以前のバージョンで返されていた。<br /><br /> 具体的には、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 では、すべてへの文字列変換で年の値が範囲外の 22007 が返されます**datetime**、OLE DB Driver for SQL Server が日付がでサポートされる範囲内にある場合、22008を返しますと**datetime2**でサポートされる範囲外**datetime**または**smalldatetime**です。|  
|**datetime**値によって秒の小数部が切り捨てられ、ない場合にラウンド丸め処理によって日が変わる。|前のバージョン[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 10.0 で、クライアントの動作**datetime**サーバーに送信された値が 1 の近似値に丸めが/300 秒です。 OLE DB Driver for SQL Server、このシナリオが原因となって秒の小数部の切り捨てが丸め処理によって日が変わる場合。|  
|秒の考えられる trunction **datetime**値。|接続する SQL Server の OLE DB ドライバーでビルドされたアプリケーション、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005年サーバーは、型識別子を DBTYPE_DBTIMESTAMP (ある datetime 列にバインドする場合は、サーバーに送信されるデータの時刻部分の秒および秒未満で切り捨てますOLE DB) または SQL_TIMESTAMP (ODBC) と小数点以下桁数は 0 です。<br /><br /> 以下に例を示します。<br /><br /> 入力データ: 1994-08-21 21:21:36.000<br /><br /> 挿入されるデータ: 1994-08-21 21:21:00.000|  
|DBTYPE_DBTIME から DBTYPE_DATE への OLE DB データ変換で日が変更されなくなる|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 より前のバージョンでは、DBTYPE_DATE の時刻部分が午前 0 時から 0.5 秒以内の場合、OLE DB の変換コードによって日が変更されました。 で OLE DB Driver for SQL Server、日は (秒の小数部が切り捨てし、丸められません) に変更されません。|  
|IBCPSession::BCColFmt 変換の変更。|OLE DB Driver for SQL Server で IBCPSession::BCOColFmt を使用して SQLDATETIME または SQLDATETIME を文字列型に変換するときに、小数部の値がエクスポートされます。 たとえば、型に変換する SQLDATETIME SQLNVARCHARMAX より前のバージョンを型[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 10.0 が返されます<br /> 1989-02-01 00:00:00 が返されます。<br />OLE DB Driver for SQL Server を返します <br />1989-02-01 00:00:00.0000000.|  
|BCP API を使用するカスタム アプリケーションで警告が表示される|指定されたフィールド長をデータ長が上回る場合、どの型の場合でも BCP API によって警告メッセージが生成されます。 以前のバージョンでは、この警告は、すべての型ではなく文字型についてのみ表示されました。|  
|空の文字列を挿入する、 **sql_variant**バインド日付/時刻型には、エラーが生成されます。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 でに空の文字列を挿入する、 **sql_variant**バインド日付/時刻型では、エラーは生成されませんでした。 OLE DB Driver for SQL Server は、このような状況に正しくエラーを生成します。|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、トリガーの実行時に異なる結果を返す場合がある|導入された変更[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]に結果が異なるときに実行するトリガーを原因となったステートメントから返されたアプリケーションが発生する可能性があります**NOCOUNT OFF**有効であった。 このような場合、アプリケーションでエラーが発生することがあります。 このエラーを解決するには、次のように設定します。 **NOCOUNT ON**トリガーまたは SQLMoreResults を呼び出し、次の結果に進みます。|  

## <a name="see-also"></a>参照   
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/oledb-driver-for-sql-server-programming.md)
