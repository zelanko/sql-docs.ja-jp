---
title: あいまいグループ化変換エディター ([接続マネージャー] タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ae31e32645c902912b80545f599fd9d187f6b052
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378890"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a>[あいまいグループ化変換エディター] ([接続マネージャー] タブ)
  **[あいまいグループ化変換エディター]** ダイアログ ボックスの **[接続マネージャー]** タブを使用すると、既存の接続を選択したり新しい接続を作成したりできます。  
  
> [!NOTE]  
>  接続によって指定されるサーバーでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が実行されている必要があります。 あいまいグループ化変換では、変換に対する完全な入力と同じサイズの一時データ オブジェクトが tempdb に作成されます。 変換の実行中は、これらの一時オブジェクトに対してサーバー クエリが発行されます。 この操作は、サーバーの全体のパフォーマンスに影響を与える可能性があります。  
  
 あいまいグループ化変換の詳細については、「 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[キャッシュなし]**  
 既存の OLE DB 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [あいまいグループ化変換を使用して類似のデータ行を識別する](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
