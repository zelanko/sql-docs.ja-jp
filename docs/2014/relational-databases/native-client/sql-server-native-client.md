---
title: SQL Server Native Client | の新機能&#39;Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 003abb67cd66d02294210ddb3f55061abcc804f4
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704142"
---
# <a name="what39s-new-in-sql-server-native-client"></a>SQL Server Native Client の新機能&#39;
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] は、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client をインストールします。 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client は存在しません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の ODBC ドライバーにはこれ以上の更新プログラムがありません。 Windows の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC Driver 11 for [!INCLUDE[msCoName](../../includes/msconame-md.md)] と呼ばれる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の ODBC ドライバーに代わるものが [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] と共にインストールされます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]ODBC driver 11 for On windows の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [Microsoft odbc driver 11 For SQL Server-windows](https://www.microsoft.com/download/details.aspx?id=36434)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の OLE DB プロバイダーは、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client で最終更新されています。 開発者が OLE DB プロバイダーを使用して最新バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するには、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client に付属している OLE DB プロバイダーを使用する必要があります。  
  
 次のトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client の重要な新機能について説明します。  
  
-   [SQL Server Native Client における LocalDB のサポート](features/sql-server-native-client-support-for-localdb.md)  
  
-   [メタデータの検出](features/metadata-discovery.md)  
  
-   [SQL Server Native Client 11.0 での UTF-16 のサポート](features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [SQL Server Native Client の HADR サポート](features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [拡張イベントログの診断情報へのアクセス](features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
 さらに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の ODBC では、Windows 7 SDK の標準 ODBC に追加された 3 つの機能もサポートされるようになりました。  
  
-   接続関連の操作での非同期実行。 詳細については、「[非同期実行](https://go.microsoft.com/fwlink/?LinkID=191493)」を参照してください。  
  
-   C データ型の機能拡張。 詳細については、「 [ODBC の C データ型](https://go.microsoft.com/fwlink/?LinkID=191495)」を参照してください。  
  
     Native Client でこの機能をサポートするために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 `SQL_C_SS_TIME2` アプリケーションで `time` `SQL_C_SS_TIMESTAMPOFFSET` `datetimeoffset` `SQL_C_BINARY` ODBC 3.8 が使用されている場合、SQLGetDescField はの代わりに (型の場合) または (の場合) を返すことができます。 詳細については、「 [ODBC の日付と時刻の機能強化に関するデータ型のサポート](features/date-and-time-improvements.md)」を参照してください。  
  
-   小さなバッファーを伴う `SQLGetData` を複数回呼び出すことによる、大きなパラメーター値の取得。 詳細については、「 [SQLGetData を使用した出力パラメーターの取得](https://go.microsoft.com/fwlink/?LinkID=191494)」を参照してください。  
  
 次のトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client の動作の変更点について説明します。  
  
-   を呼び出す場合 `ICommandWithParameters::SetParameterInfo` 、 *pwszName*パラメーターに渡される値は有効な識別子である必要があります。 詳細については、「 [ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md)」を参照してください。  
  
-   `SQLDescribeParam` は、ODBC 仕様に準拠した値を一貫して返すようになりました。 詳細については、「 [SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md)」を参照してください。  
  
-   [文字変換処理での ODBC ドライバーの動作の変更](features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](features/sql-server-native-client-features.md)  
  
  
