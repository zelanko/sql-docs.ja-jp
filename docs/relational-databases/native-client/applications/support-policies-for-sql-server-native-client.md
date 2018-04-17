---
title: SQL Server Native Client のサポート ポリシー |Microsoft ドキュメント
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 09c80cf4-23e6-4027-a24f-cdb9c87af811
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2406104036881166398e7122613579b65217ce0e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="support-policies-for-sql-server-native-client"></a>SQL Server Native Client のサポート ポリシー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ここでは、さまざまなデータ アクセス コンポーネントを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で使用する方法について説明します。  
  
## <a name="server-support"></a>サーバー サポート  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 への接続をサポートしている[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]、および[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]です。  
  
## <a name="supported-operating-system-versions"></a>サポートされるオペレーティング システムのバージョン  
 次の表に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をサポートするオペレーティング システムの一覧を示します。  
  
|SQL Server Native Client のバージョン|サポートされるオペレーティング システム|  
|--------------------------------------|---------------------------------|  
|SQL Server Native Client (SQL Server 2005)|Microsoft Windows 2000 Service Pack 4 以降<br /><br /> Microsoft Windows Server 2003 以降<br /><br /> Microsoft Windows XP Service Pack 1 またはそれ以降<br /><br /> Microsoft Windows Vista ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 2 以降が必要)<br /><br /> Microsoft Windows Server 2008 R2 (必要[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Service Pack 2、またはそれ以降)|  
|SQL Server Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)])|Microsoft Windows Server 2003 Service Pack 2 以降<br /><br /> Microsoft Windows XP Service Pack 2 以降<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2|  
|SQL Server Native Client 10.5 ([!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)])|Microsoft Windows Server 2003 Service Pack 2 以降<br /><br /> Microsoft Windows XP Service Pack 2 以降<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7|  
|SQL Server Native Client 11.0 ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] および [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)])|Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7<br /><br /> Microsoft Windows 8<br /><br /> Microsoft Windows Server 2012|  
  
## <a name="ado-support-policies"></a>ADO サポート ポリシー  
 ADO アプリケーションでは、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降の機能を必要としない場合に、Windows に付属している SQLOLEDB OLE DB プロバイダーを使用できます。  
  
 ADO アプリケーションでのバージョンを使用できる[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client に含まれる[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。 また、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に含まれている [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client 11.0 も使用できますが、これを使用する場合は、接続文字列に `DataTypeCompatibility=80` を指定する必要があります。 `DataTypeCompatibility=80` が接続文字列に含まれている場合は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の機能しか使用できません。  
  
## <a name="bcp-support-policies"></a>BCP サポート ポリシー  
 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、bcp.exe は、bcp.exe が提供された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンより 3 バージョン前までの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ ファイルをサポートします。  
  
## <a name="odbc-support-policies"></a>ODBC サポート ポリシー  
 アプリケーションは、Windows オペレーティング システムに付属している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC ドライバーを使用する必要があります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、アプリケーションが特定のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client との互換性が保証されている場合に使用できます。  
  
## <a name="ole-db-support-policies"></a>OLE DB サポート ポリシー  
 アプリケーションは Windows オペレーティング システムに付属している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB プロバイダーを使用する必要があります。 アプリケーションと特定のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client との互換性が保証されている場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用することができます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client との互換性が保証されていない OLE DB アプリケーションでは、接続文字列に `DataTypeCompatibility=80` を指定すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用できます。  
  
 OLE DB サービス コンポーネントを使用している OLE DB アプリケーションでは、接続文字列に `DataTypeCompatibility=80` を指定した場合のみ、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用できます。 ただし、機能の後に追加[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ここで使用可能になります。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client でアプリケーションの構築](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
