---
title: SQL Server Data Tools のコンポーネントの削除 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 124b4f4f591966d8dc5294f3150892091f71ba74
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094866"
---
# <a name="removing-sql-server-data-tools-components"></a>SQL Server Data Tools のコンポーネントの削除
SSDT または Visual Studio をアンインストールするとき、SQL Server Data Tools (SSDT) のいくつかのコンポーネントは削除されません。  
  
次の Windows インストーラー パッケージ (.msi) は、SSDT または Visual Studio がアンインストールされたときにコンピューターから削除されません。 これらのコンポーネントを削除すると、サポートされていない状態の別のバージョンの Visual Studio をインストールできます。 これらのコンポーネントを削除する場合は、Windows の [プログラムの追加と削除] を使用してください。  
  
-   MicrosoftSQL Server Data Tools (SSDT.msi)  
  
-   MicrosoftSQL Server Data Tools ビルド ユーティリティ (SSDTBuildUtilities.msi)  
  
-   Prerequisites for SSDT (SSDTDBSvcExternals.msi)  
  
次の共有コンポーネントは、他の製品によって使用されている可能性があり、SSDT のアンインストール後もコンピューター上に残ります。  
  
-   SQL Server データ層アプリケーション フレームワーク (DACFramework.msi)  
  
-   SQL Server 管理オブジェクト (SharedManagementObjects.msi)  
  
-   SQL ServerTransact\-SQL 言語サービス (TSqlLanguageService.msi)  
  
-   MicrosoftSQL Server System CLR Types for SQL Server (SQLSysClrTypes.msi)  
  
-   SQL ServerTransact\-SQL ScriptDom (SQLDom.msi)  
  
-   SQL ServerTransact\-SQL Compiler Service (SQLLs.msi)  
  
