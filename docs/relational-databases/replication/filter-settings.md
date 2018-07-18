---
title: フィルターの設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ced3fd26c7391eb481366200385235ab5d699c80
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356374"
---
# <a name="filter-settings"></a>[フィルターの設定]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[フィルターの設定]** ダイアログ ボックスを使用すると、レプリケーション モニターのグリッドのフィルターを定義できます。 たとえば、アクティブなサブスクリプションのみを **[すべてのサブスクリプション]** タブに表示するには、 **[列名]** 列から **[状態]** を選択し、 **[演算子]** 列から **[等しい]** を選択し、 **[値 1]** 列から **[アクティブ]** を選択します。 1 つ以上の列に基づくフィルターを定義したら、フィルター条件に一致する行のサブセットのみがグリッドに表示されるようにフィルターが適用されます。  
  
## <a name="options"></a>および  
 **[状態]**  
 フィルター選択する列の名前を選択します。 1 つ以上の列をフィルター処理の基にすることができます。  
  
 **[等しい]**  
 フィルターで使用する演算子 (たとえば、 **[次の値以下]**) を選択します。  
  
 **[値 1]** および **[値 2]**  
 フィルターの値を入力または選択します。 ほとんどの演算子は **[値 1]** 列に値を入力するだけで済みますが、 **[次の値の間]** と **[次の値の範囲外]** の操作は、 **[値 2]** 列にも値を入力する必要があります。  
  
 **[フィルターのクリア]**  
 このボタンをクリックすると、定義されているすべてのフィルターがクリアされます。 単一のフィルターを削除するには、フィルター行を選択して Del キーを押します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
