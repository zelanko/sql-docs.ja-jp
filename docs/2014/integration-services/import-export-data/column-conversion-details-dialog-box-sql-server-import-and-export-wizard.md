---
title: '[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cd97a1bb27858b9107312f3ac32ea61ce07f415b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083219"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード)
  使用して、**列変換の詳細** ダイアログ ボックスで、個々 の列に関する詳細な変換情報を確認します。 この変換情報には、変換元および変換先での列のデータ型や、ウィザードが実行する変換が含まれます。 このページには、必要なデータ型変換を判断するためにウィザードで使用されるデータ型マッピング ファイルも一覧表示されます。 これらのデータ型マッピング ファイルは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってセットアップ時にインストールされます。  
  
 **列変換の詳細 ダイアログ ボックスを開く**  
  
1.  **データ型の問題のレビュー**のページ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードで、**テーブル**一覧で、テーブルを選択します。  
  
2.  **データ型マッピング**リストで、変換の詳細を表示する列を含む行をダブルクリックします。  
  
 詳細について、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードを参照してください[SQL Server インポートおよびエクスポート ウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)です。 について、ウィザードを起動するオプションおよびウィザードが正常に実行するための権限については、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)です。  
  
 目的、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードはデータ ソースからの保存先にコピーします。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
  