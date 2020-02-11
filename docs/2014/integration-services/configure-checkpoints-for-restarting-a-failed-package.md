---
title: 失敗したパッケージを再起動するためのチェックポイントを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e22e47af568ecf723b54a35fb6b83bd5ce74e333
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060769"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a>失敗したパッケージを再開するためのチェックポイントを構成する
  パッケージ全体を再実行するのではなく、障害が発生した時点からパッケージを再開するように [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを構成するには、チェックポイントに適用するプロパティを設定します。  
  
### <a name="to-configure-a-package-to-restart"></a>パッケージを再開するように構成するには  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、構成するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  **ソリューションエクスプローラー**で、パッケージをダブルクリックして開きます。  
  
3.  
  **[制御フロー]** タブをクリックします。  
  
4.  制御フローのデザイン画面の背景で任意の場所を右クリックし、 **[プロパティ]** をクリックします。  
  
5.  SaveCheckpoints プロパティをに`True`設定します。  
  
6.  CheckpointFileName プロパティにチェックポイント ファイルの名前を入力します。  
  
7.  CheckpointUsage プロパティを、次の 2 つの値のどちらかに設定します。  
  
    -   チェックポイントから常にパッケージを再開するには、`Always` を選択します。  
  
        > [!IMPORTANT]  
        >  チェックポイント ファイルが使用できない場合はエラーが発生します。  
  
    -   チェックポイント ファイルが使用できる場合のみパッケージを再開するには、`IfExists` を選択します。  
  
8.  パッケージが再開できる地点のタスクおよびコンテナーを構成します。  
  
    -   タスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。  
  
    -   選択した各タスク`True`およびコンテナーに対して、FailPackageOnFailure プロパティをに設定します。  
  
## <a name="see-also"></a>参照  
 [チェックポイントを使用してパッケージを再開する](packages/restart-packages-by-using-checkpoints.md)  
  
  
