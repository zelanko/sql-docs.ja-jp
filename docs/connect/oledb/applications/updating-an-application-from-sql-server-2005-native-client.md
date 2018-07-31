---
title: SQL Server 2005 Native Client からのアプリケーションの更新 | Microsoft Docs
description: SQL Server 2005 Native Client からのアプリケーションの更新
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 915b098a6807e4c81f74839a62d6e32d5ced08af
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108804"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>SQL Server 2005 Native Client からのアプリケーションの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  このトピックでは、以降の SQL Server の OLE DB ドライバーにおける重大な変更を説明[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client に[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]します。  

 Microsoft Data Access Components (MDAC) を OLE DB Driver for SQL Server にアップグレードした場合も、一部の動作で違いが生じます。 詳細については、次を参照してください。 [MDAC から SQL Server の OLE DB ドライバーへのアプリケーションの更新](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)します。  

 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] に付属する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] に付属する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0。  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に付属する [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 10.5。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] および [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] に付属する [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client 11.0。  

|比較すると、SQL Server の OLE DB ドライバーの動作を変更して[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]Native Client|[説明]|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB によって定義された有効桁数までしか埋め込まれない|OLE DB Driver for SQL Server、サーバーへの変換後のデータの送信先の変換をデータの最大長までしかの後ろにゼロで埋める**datetime**値。 SQL Server Native Client 9.0 では、9 桁まで埋め込まれていました。|  
|ICommandWithParameter::SetParameterInfo DBTYPE_DBTIMESTAMP を検証します。|OLE DB Driver for SQL Server、OLE DB 要件が実装*bScale*で ICommandWithParameter::SetParameterInfo DBTYPE_DBTIMESTAMP の秒の小数部の精度に設定されます。|  
|**Sp_columns**ストアド プロシージャ **"NO"** の代わりに **"NO"** によって IS_NULLABLE 列にします。|OLE DB Driver for SQL Server で**sp_columns**ストアド プロシージャ **"NO"** の代わりに **"NO"** によって IS_NULLABLE 列。|  
|日付が範囲外の場合に別のエラーが返される|**Datetime**の種類別のエラー番号によって返される OLE DB Driver for SQL Server、範囲外の日付の以前のバージョンで返されていた。<br /><br /> 具体的には、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 では、すべてへの文字列変換で年の値が範囲外の場合は 22007 が返されます**datetime**日付がでサポートされる範囲内にある場合、22008が返さOLEDBDriverforSQLServerと**datetime2**でサポートされる範囲外**datetime**または**smalldatetime**します。|  
|丸め処理によって日が変わる場合に **datetime** 値では秒の小数部が丸められずに切り捨てられる。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 より前のバージョンでは、サーバーに送信される **datetime** 値は、クライアントによって 1/300 秒単位に丸められていました。 OLE DB Driver for SQL Server では、このシナリオは、丸め処理によって日が変わる場合に、秒の小数部の切り捨てとされます。|  
|秒の可能な切り捨て**datetime**値。|OLE DB Driver for SQL Server でビルドしたアプリケーションが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 サーバーに接続する場合、型識別子を DBTYPE_DBTIMESTAMP (OLE DB) または SQL_TIMESTAMP (ODBC) に設定し、小数点以下桁数を 0 に設定して datetime 列にバインドすると、サーバーに送信されるデータの時刻部分の秒および秒の小数部が切り捨てられます。<br /><br /> 例 :<br /><br /> 入力データ: 1994-08-21 21:21:36.000<br /><br /> 挿入されるデータ: 1994-08-21 21:21:00.000|  
|DBTYPE_DBTIME から DBTYPE_DATE への OLE DB データ変換で日が変更されなくなる|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 より前のバージョンでは、DBTYPE_DATE の時刻部分が午前 0 時から 0.5 秒以内の場合、OLE DB の変換コードによって日が変更されました。 で OLE DB Driver for SQL Server を日は (秒の小数部が切り捨てし、丸められません) は変更されません。|  
|IBCPSession::BCColFmt 変換の変更。|OLE DB driver for SQL Server、IBCPSession::BCOColFmt を使用して SQLDATETIME または SQLDATETIME を文字列型に変換する場合、小数部の値がエクスポートされます。 たとえば、SQLDATETIME 型を SQLNVARCHARMAX 型に変換すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 より前のバージョンでは、<br /> 1989-02-01 00:00:00 が返されます。<br />OLE DB Driver for SQL Server では、 <br />1989-02-01 00:00:00.0000000 が返されます。|  
|BCP API を使用するカスタム アプリケーションで警告が表示される|指定されたフィールド長をデータ長が上回る場合、どの型の場合でも BCP API によって警告メッセージが生成されます。 以前のバージョンでは、この警告は、すべての型ではなく文字型についてのみ表示されました。|  
|日付型または時刻型としてバインドされた **sql_variant** に空の文字列を挿入するとエラーが生成される。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 では、日付型または時刻型としてバインドされた **sql_variant** に空の文字列を挿入してもエラーは生成されませんでした。 OLE DB Driver for SQL Server は、このような状況に正しくエラーを生成します。|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、トリガーの実行時に異なる結果を返す場合がある|[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] で導入された変更により、**NOCOUNT OFF** が有効なときに、トリガーを実行させたステートメントからアプリケーションに返される結果が異なる可能性があります。 このような場合、アプリケーションでエラーが発生することがあります。 このエラーを解決するには、次のように設定します。 **NOCOUNT ON**トリガーします。|  

## <a name="see-also"></a>参照   
 [OLE DB Driver for SQL Server](../../oledb/oledb-driver-for-sql-server.md)
