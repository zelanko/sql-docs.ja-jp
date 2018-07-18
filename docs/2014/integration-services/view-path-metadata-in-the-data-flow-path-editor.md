---
title: パスのメタデータをデータ フロー パス エディターで表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [Integration Services]
- paths [Integration Services], metadata
ms.assetid: 25cf8bdd-8691-4caa-96b6-3081b2f37dea
caps.latest.revision: 23
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7163b07ea791330299603e9b90d5eca7b1c33b4f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289148"
---
# <a name="view-path-metadata-in-the-data-flow-path-editor"></a>データ フロー パス エディターでパスのメタデータを表示する
  パスは、2 つのデータ フロー コンポーネントを連結します。 パスのメタデータを表示する場合、データ フローには、2 つ以上の連結されたデータ フロー コンポーネントをあらかじめ含めておく必要があります。 詳細については、「 [データ フローでコンポーネントを追加または削除する](data-flow/add-or-delete-a-component-in-a-data-flow.md) 」と「 [データ フロー内でコンポーネントを連結する](data-flow/connect-components-in-a-data-flow.md)」を参照してください。  
  
### <a name="to-view-path-metadata"></a>パスのメタデータを表示するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブをクリックし、パスをダブルクリックします。  
  
4.  **[データ フロー パス エディター]** ダイアログ ボックスで、 **[メタデータ]** をクリックします。  
  
5.  パスのメタデータが表示されます。メタデータには、各列の列名、データ型、有効桁数、小数点以下桁数、データ長、コード ページ、および基になるコンポーネントの名前が含まれます。  
  
6.  メタデータをコピーするには、 **[クリップボードにコピー]** をクリックします。  
  
7.  [**OK**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [Integration Services のパス](data-flow/integration-services-paths.md)   
 [データ フロー](data-flow/data-flow.md)  
  
  
