---
title: SQL Server Data Tools のコンポーネントの削除 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b114b99b816e10bc004cea8d60c56d296053c7c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685470"
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
  
