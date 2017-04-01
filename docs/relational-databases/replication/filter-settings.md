---
title: "[フィルターの設定] | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.filtersettings.f1"
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
caps.latest.revision: 6
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 6
---
# [フィルターの設定]
  **[フィルターの設定]** ダイアログ ボックスを使用すると、レプリケーション モニターのグリッドのフィルターを定義できます。 たとえば、アクティブなサブスクリプションのみを **[すべてのサブスクリプション]** タブに表示するには、 **[列名]** 列から **[状態]** を選択し、 **[演算子]** 列から **[等しい]** を選択し、 **[値 1]** 列から **[アクティブ]** を選択します。 1 つ以上の列に基づくフィルターを定義したら、フィルター条件に一致する行のサブセットのみがグリッドに表示されるようにフィルターが適用されます。  
  
## オプション  
 **列名**  
 フィルター選択する列の名前を選択します。 1 つ以上の列をフィルター処理の基にすることができます。  
  
 **演算子**  
 フィルターは、演算子を選択します。 **以下に**します。  
  
 **Value1** と **Value2**  
 フィルターの値を入力または選択します。 ほとんどの演算子は **[値 1]** 列に値を入力するだけで済みますが、 **[次の値の間]** と **[次の値の範囲外]** の操作は、 **[値 2]** 列にも値を入力する必要があります。  
  
 **[フィルターのクリア]**  
 このボタンをクリックすると、定義されているすべてのフィルターがクリアされます。 単一のフィルターを削除するには、フィルター行を選択して Del キーを押します。  
  
## 参照  
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  