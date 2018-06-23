---
title: パッケージの配置 (SSIS) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7a732d2b3c8371d0bb5637cbe19101640e8d81a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084780"
---
# <a name="package-deployment-ssis"></a>パッケージの配置 (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、開発コンピューターから実稼働サーバーまたは他のコンピューターへのパッケージの配置を簡素化するツールとウィザードが含まれています。  
  
 パッケージ配置プロセスは、次の 4 段階で行います。  
  
1.  最初の手順は省略可能です。この手順では、実行時にパッケージのプロパティ要素を更新するパッケージ構成を作成します。 この構成は、パッケージを配置する際に自動的に適用されます。  
  
2.  2 番目の手順は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトをビルドして、パッケージ配置ユーティリティを作成することです。 プロジェクトの配置ユーティリティには、配置するパッケージが含まれます。  
  
3.  3 番目の手順は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトのビルド時に作成された配置フォルダーを配置先コンピューターにコピーすることです。  
  
4.  4 番目の手順は、配置先コンピューターでパッケージ インストール ウィザードを実行し、ファイル システムまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにパッケージをインストールすることです。  
  
## <a name="related-tasks"></a>Related Tasks  
 配置ユーティリティを作成する方法については、「 [Create a Deployment Utility](../create-a-deployment-utility.md)」 (配置ユーティリティの作成) を参照してください。  
  
 配置ユーティリティを使用してパッケージを配置する方法については、「 [配置ユーティリティを使用してパッケージを配置する](../deploy-packages-by-using-the-deployment-utility.md)」を参照してください。  
  
 パッケージ構成を作成する方法の詳細については、「 [パッケージ構成を作成する](../create-package-configurations.md)」を参照してください。  
  
  