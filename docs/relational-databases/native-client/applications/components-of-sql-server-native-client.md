---
title: "SQL Server Native Client のコンポーネント |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3148b8910db157a6cc6befe2b742e6d0c0cd1016
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="components-of-sql-server-native-client"></a>SQL Server Native Client のコンポーネント
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client には、次のコンポーネントが含まれています。  
  
|コンポーネント|Description|  
|---------------|-----------------|  
|sqlncli11.dll|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client のすべての機能を含む DLL (ダイナミック リンク ライブラリ) ファイル。 このファイルには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが含まれます。|  
|sqlnclir11.rll|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ライブラリに付随するリソース ファイル。|   
|sqlncli.h|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用する場合に必要となる、新しいすべての定義を含む [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイル。 このヘッダー ファイルは、odbcss.h ヘッダー ファイルと sqloledb.h ヘッダー ファイルの両方に置き換わるものです。<br /><br /> 注: は、sqlncli.h と odbcss.h を同じプログラムで参照することはできませんが、sqloledb.h を最初に定義されている限り、sqlncli.h と sqloledb.h 同じプログラム内でを参照することができます。|  
|sqlncli11.lib|直接の呼び出しに必要なライブラリ ファイル、 **bcp**ユーティリティ関数の一部である、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。<br /><br /> 注: プログラミング コードで sqlncli11.lib ファイルを参照する場合は sqlncli11.dll ファイルがシステム パス、および構成するユーザーのシステム パスであるかどうかを確認するアプリケーションを使用します。|  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client を使用したアプリケーションのビルド](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
