---
title: Azure HDInsight 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d3995c1b0f830277441e236d375c87f21f8d42f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221912"
---
# <a name="azure-hdinsight-connection-manager"></a>Azure HDInsight 接続マネージャー
**Azure HDInsight 接続マネージャー**により、SSIS パッケージは Azure HDInsight クラスターに接続できます。

**Azure HDInsight 接続マネージャー**を作成して構成するには、以下の手順のようにします。

1. **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureHDInsight]** を選び、**[追加]** をクリックします。
2. **[Azure HDInsight Connection Manager Editor]\(Azure HDInsight 接続マネージャー エディター\)** ダイアログ ボックスで、接続先の HDInsight クラスターの **[Cluster DNS name]\(クラスター DNS 名\)** (プロトコル プレフィックスなし)、**[ユーザー名]**、**[パスワード]** を指定します。
3. **[OK]** をクリックしてダイアログ ボックスを閉じます。
4. 作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。
