---
title: '[データ ビューアー] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
author: janinezhang
ms.author: janinez
ms.openlocfilehash: f45a99b149feb0c0609aac88660ad7e62ca425f2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84916022"
---
# <a name="data-viewer"></a>[データ ビューアー]
  パスがデータ ビューアーを使用するように構成されている場合、データ ビューアーはデータが 2 つのデータ フロー コンポーネントを移動するときに、バッファーによるデータ バッファーを表示します。  
  
## <a name="options"></a>オプション  
 **緑色の矢印**  
 クリックすると、次のバッファーのデータが表示されます。 データが 1 つのバッファーに移動される場合、このオプションは使用できません。  
  
 **[デタッチ]**  
 データ ビューアーをデタッチします。  
  
 **注** &#xA0;&#xA0;&#xA0;データ ビューアーをデタッチしてもデータ ビューアーは削除されません。 データ ビューアーがデタッチされた場合、データはパスを流れますが、ビューアー内のデータを各バッファーのデータに一致させる更新は行われません。  
  
 **[アタッチ]**  
 データ ビューアーをアタッチします。  
  
 **注** &#xA0;&#xA0;&#xA0;アタッチされたデータ ビューアーは、データ フロー内の各バッファーからの情報を表示してから、一時停止します。 緑色の矢印を使用して次のバッファーに進むことができます。  
  
 **[データのコピー]**  
 現在のバッファーのデータをクリップボードにコピーします。  
  
## <a name="see-also"></a>参照  
 [データ フローのデバッグ](../troubleshooting/debugging-data-flow.md)  
  
  
