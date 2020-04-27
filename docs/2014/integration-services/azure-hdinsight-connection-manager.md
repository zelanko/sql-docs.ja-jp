---
title: Azure HDInsight 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dfeade50b36e39f9a4bfa354f71a6bca53e03c16
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66061366"
---
# <a name="azure-hdinsight-connection-manager"></a>Azure HDInsight 接続マネージャー
**Azure HDInsight 接続マネージャー**により、SSIS パッケージは Azure HDInsight クラスターに接続できます。

**Azure HDInsight 接続マネージャー**を作成して構成するには、以下の手順のようにします。

1. **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureHDInsight]** を選び、**[追加]** をクリックします。
2. **[Azure HDInsight Connection Manager Editor]\(Azure HDInsight 接続マネージャー エディター\)** ダイアログ ボックスで、接続先の HDInsight クラスターの **[Cluster DNS name]\(クラスター DNS 名\)** (プロトコル プレフィックスなし)、**[ユーザー名]**、**[パスワード]** を指定します。
3. **[OK]** をクリックしてダイアログ ボックスを閉じます。
4. 作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。
