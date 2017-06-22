---
title: "Rsmodelgenerationerror-reporting Services エラー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
caps.latest.revision: 17
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 658d9bdaffa05e3bf287b38953bc2e318da7d319
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="rsmodelgenerationerror---reporting-services-error"></a>rsModelGenerationError - Reporting Services エラー
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|rsRenderingError|  
|イベント ソース|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|コンポーネント|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|メッセージ テキスト|モデルの生成中にエラーが発生しました。 (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## <a name="explanation"></a>説明  
 レポート モデルを生成できませんでした。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 以前のバージョンでは、このエラーは、System.Data.DataSet オブジェクトでデータベース スキーマ内のテーブルまたはリレーションシップを処理できない場合に表示される可能性があります。たとえば、1 つのテーブル内の同じ列に 2 つの外部キーが定義されている場合などです。  
  
## <a name="user-action"></a>ユーザーの操作  
 このメッセージが表示される原因となった具体的な理由を特定するには、\Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles にあるレポート サーバーのログ ファイルを確認します。  
  
## <a name="internal-only"></a>内部使用のみ  
  
