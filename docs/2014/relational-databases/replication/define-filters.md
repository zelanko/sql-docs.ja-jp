---
title: '[フィルターの定義] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f7b82b3450727d36a36186453e366625ebecbde2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721394"
---
# <a name="define-filters"></a>[フィルターの定義]
  **[フィルターの定義]** ダイアログ ボックスを使用すると、グリッド内で競合するサブセットを確認するために、データ競合に適用するフィルターを定義できます。 フィルターを定義するには、 **[演算子]** ボックスで演算子を選択し、値を入力します。 たとえば、競合で負けたサーバーが **ReplTest1**の競合だけを表示するには、 **[演算子]** ボックスで **[等しい]** を選択し、1 番目の **[値]** 列に「 **ReplTest1** 」と入力します。  
  
## <a name="options"></a>オプション  
 **[オペレーター]**  
 フィルターで使用する演算子 (たとえば、 **[次の値以下]** ) を選択します。  
  
 **Value**  
 フィルターの値を入力します。 ほとんどの演算子は 1 番目の **[値]** 列に値を入力するだけで済みますが、 **[次の値の間]** と **[次の値の範囲外]** の操作は、2 つの **[値]** 列に値を入力する必要があります。  
  
 **Clear**  
 このボタンをクリックすると、既に定義されているすべてのフィルターがクリアされます。  
  
## <a name="see-also"></a>参照  
 [[Microsoft レプリケーション競合表示モジュール] (マージ レプリケーション)](microsoft-replication-conflict-viewer-merge-replication.md)   
 [Microsoft レプリケーション競合表示モジュール (トランザクション レプリケーション)](microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
