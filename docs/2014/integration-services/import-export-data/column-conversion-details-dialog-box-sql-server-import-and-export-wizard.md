---
title: '[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: dd4e53a1e6485d74ba2aff4039108b357d9c0c92
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966235"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード)
  [**列変換の詳細**] ダイアログボックスを使用すると、個々の列に関する詳細な変換情報を確認できます。 この変換情報には、変換元および変換先での列のデータ型や、ウィザードが実行する変換が含まれます。 このページには、必要なデータ型変換を判断するためにウィザードで使用されるデータ型マッピング ファイルも一覧表示されます。 これらのデータ型マッピング ファイルは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってセットアップ時にインストールされます。  
  
 **[列変換の詳細] ダイアログ ボックスを開くには**  
  
1.  インポートおよびエクスポートウィザードの [**データ型の問題の確認**] ページで、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **テーブル**] ボックスの一覧からテーブルを選択します。  
  
2.  [**データ型マッピング**] の一覧で、変換の詳細を表示する列が含まれている行をダブルクリックします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポートウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
  
