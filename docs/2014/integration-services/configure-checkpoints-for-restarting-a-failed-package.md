---
title: 失敗したパッケージを再開するためのチェックポイントの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9204220c7ea32c59f75785ad0b50fa050a47840f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123402"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a>失敗したパッケージを再開するためのチェックポイントを構成する
  パッケージ全体を再実行するのではなく、障害が発生した時点からパッケージを再開するように [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを構成するには、チェックポイントに適用するプロパティを設定します。  
  
### <a name="to-configure-a-package-to-restart"></a>パッケージを再開するように構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、構成するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  **ソリューション エクスプローラー**で、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックします。  
  
4.  制御フローのデザイン画面の背景で任意の場所を右クリックし、 **[プロパティ]** をクリックします。  
  
5.  SaveCheckpoints プロパティを設定`True`します。  
  
6.  CheckpointFileName プロパティにチェックポイント ファイルの名前を入力します。  
  
7.  CheckpointUsage プロパティを、次の 2 つの値のどちらかに設定します。  
  
    -   チェックポイントから常にパッケージを再開するには、`Always` を選択します。  
  
        > [!IMPORTANT]  
        >  チェックポイント ファイルが使用できない場合はエラーが発生します。  
  
    -   選択`IfExists`チェックポイント ファイルが使用可能な場合にのみ、パッケージを再開します。  
  
8.  パッケージが再開できる地点のタスクおよびコンテナーを構成します。  
  
    -   タスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。  
  
    -   FailPackageOnFailure プロパティを設定`True`選択した各タスクとコンテナー。  
  
## <a name="see-also"></a>参照  
 [チェックポイントを使用してパッケージを再開する](packages/restart-packages-by-using-checkpoints.md)  
  
  
