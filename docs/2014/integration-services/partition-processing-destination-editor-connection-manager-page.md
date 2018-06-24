---
title: パーティション処理変換先エディター (接続マネージャー ページ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cf99c71785b362f185b5ce4b6b317fb7369a3666
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071233"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a>[パーティション処理変換先エディター] ([接続マネージャー] ページ)
  **[パーティション処理変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスへの接続を指定できます。  
  
 パーティション処理変換先の詳細については、「 [Partition Processing Destination](data-flow/partition-processing-destination.md)」を参照してください。  
  
> [!NOTE]  
>  ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。  テーブル モデルで入力列をパーティション列にマップすることはできません。 代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。  
  
## <a name="options"></a>および  
 **Connection manager**  
 既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 **利用可能なパーティションの一覧**  
 処理するパーティションを選択します。  
  
 **[処理方法]**  
 処理方法を選択します。 このオプションの既定値は **[完全]** です。  
  
|値|説明|  
|-----------|-----------------|  
|[追加 (増分)]|パーティションの増分処理を実行します。|  
|[完全]|パーティションの完全処理を実行します。|  
|[データのみ]|パーティションの更新処理を実行します。|  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [パーティション処理変換先エディター &#40;[マッピング] ページ&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)   
 [パーティション処理変換先エディター &#40;[詳細] ページ&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  