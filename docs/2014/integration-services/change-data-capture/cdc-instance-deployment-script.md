---
title: '[CDC インスタンス配置スクリプト] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6fa3ba6fec2e29b48e86b3771bd081037381df6d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52811424"
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
 [CDC 用の SQL Server の準備](prepare-sql-server-for-cdc.md)  
  
  
