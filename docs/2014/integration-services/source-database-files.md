---
title: ソース データベースのファイル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
caps.latest.revision: 16
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9bad26723ccb553144359e77154804cf2ab11982
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160683"
---
# <a name="source-database-files"></a>[転送元のデータベース ファイル]
  **[転送元のデータベース ファイル]** ダイアログ ボックスを使用すると、ソース サーバーのデータベース ファイルの名前と場所を表示したり、データベース転送タスクのネットワーク ファイル共有の場所を指定したりできます。 このタスクの詳細については、「 [データベース転送タスク](control-flow/transfer-database-task.md)」を参照してください。  
  
 このダイアログ ボックスにソース サーバーのデータベース ファイルの名前と場所を入力するには、最初に **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページで **[SourceConnection]** および **[SourceDatabaseName]** を指定します。  
  
## <a name="options"></a>および  
 **[転送元ファイル]**  
 転送する対象のソース サーバーのデータベース ファイル名です。 **[転送元ファイル]** は読み取り専用です。  
  
 **[同期元フォルダー]**  
 転送する対象データベース ファイルが存在する転送元サーバーのフォルダーです。 **[転送元フォルダー]** は読み取り専用です。  
  
 **[ネットワーク ファイル共有]**  
 データベース ファイルの転送元となるソース サーバーのネットワーク共有フォルダーです。 **[ネットワーク ファイル共有]** は、データベースをオフライン モードで転送する場合に使用します。 **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページの **[Method]** に、 **[DatabaseOffline]** を指定します。  
  
 ネットワーク ファイル共有の場所を入力するか、 **[...]** をクリックしてネットワーク ファイル共有の場所を見つけます。  
  
 オフライン モードでデータベースを転送すると、データベースは転送先サーバーに転送される前に、転送元サーバーの **[ネットワーク ファイル共有]** の場所にコピーされます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [データベース転送タスク エディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [データベース転送タスク エディター&#40;データベース ページ&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
