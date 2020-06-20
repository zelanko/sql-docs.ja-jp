---
title: ソースデータベースファイル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bb40764ee279d98b6b63906ed08b26afe156aee4
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84962862"
---
# <a name="source-database-files"></a>[転送元のデータベース ファイル]
  **[転送元のデータベース ファイル]** ダイアログ ボックスを使用すると、ソース サーバーのデータベース ファイルの名前と場所を表示したり、データベース転送タスクのネットワーク ファイル共有の場所を指定したりできます。 このタスクの詳細については、「 [データベース転送タスク](control-flow/transfer-database-task.md)」を参照してください。  
  
 このダイアログ ボックスにソース サーバーのデータベース ファイルの名前と場所を入力するには、最初に **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページで **[SourceConnection]** および **[SourceDatabaseName]** を指定します。  
  
## <a name="options"></a>オプション  
 **ソースファイル**  
 転送する対象のソース サーバーのデータベース ファイル名です。 **[転送元ファイル]** は読み取り専用です。  
  
 **[同期元フォルダー]**  
 転送する対象データベース ファイルが存在する転送元サーバーのフォルダーです。 **[転送元フォルダー]** は読み取り専用です。  
  
 **[ネットワーク ファイル共有]**  
 データベース ファイルの転送元となるソース サーバーのネットワーク共有フォルダーです。 [**データベース転送タスクエディター** ] ダイアログボックスの [**データベース**] ページで [**メソッド**] に [ **databaseoffline** ] を指定して、データベースをオフラインモードで転送する場合は、[**ネットワークファイル共有**] を使用します。  
  
 ネットワーク ファイル共有の場所を入力するか、参照ボタン **([...])** をクリックしてネットワーク ファイル共有の場所を見つけます。  
  
 オフライン モードでデータベースを転送すると、データベースは転送先サーバーに転送される前に、転送元サーバーの **[ネットワーク ファイル共有]** の場所にコピーされます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [データベース転送タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [データベース転送タスク エディター ([データベース] ページ)](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
