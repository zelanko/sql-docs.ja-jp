---
title: '[CDC インスタンス配置スクリプト] | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: change-data-capture
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eaa5e76954f4ad9f694128d72fb647ee72395610
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="cdc-instance-deployment-script"></a>[CDC インスタンス配置スクリプト]
  CCD インスタンス配置スクリプトを表示する [CDC インスタンス配置スクリプト] ダイアログ ボックスです。 このスクリプトは、すべてのアーティファクトが異なる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにある CDC データベースを再作成するために使用できます。  
  
 配置スクリプトの終了時に、次のことを確認する必要があります。  
  
-   配置スクリプトでは、Oracle CDC Service 構成コンソールを使用することにより、またはプログラムが作成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 準備スクリプト **を使用することにより、ターゲットの** インスタンスが Oracle CDC に対して準備されたと仮定します。  
  
-   スクリプトのうち、CDC に対してデータベースを有効にするために使用される部分は、 `sysadmin`によって実行する必要があります。  
  
-   スクリプトでは、Oracle のログ マイニング パスワードは保持されません。 このパスワードは、スクリプトが実行され、Oracle CDC Service が開始された後に、手動で設定する必要があります。  
  
 **[CDC インスタンス配置スクリプト]** ダイアログ ボックスで次のオプションを選択します。  
  
 **[名前を付けて保存]**  
 任意の場所に保存できるテキスト ファイルにスクリプトを保存します。 スクリプトを含むファイルを他の任意のサーバーにコピーして、そのサーバーで実行できます。  
  
 **[コピー]**  
 スクリプトをクリップボードにコピーします。 その後、スクリプトを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または任意のテキスト エディターに貼り付けて、後でスクリプトを実行できます。  
  
## <a name="see-also"></a>参照  
 [CDC 用の SQL Server の準備](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
