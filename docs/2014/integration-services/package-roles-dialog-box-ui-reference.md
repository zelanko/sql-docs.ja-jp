---
title: パッケージのロール ダイアログ ボックスの UI リファレンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ad91939638592cfbd1265bd77bff13b1d60b093a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084571"
---
# <a name="package-roles-dialog-box-ui-reference"></a>[パッケージのロール] ダイアログ ボックスの UI リファレンス
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の **[パッケージのロール]** ダイアログ ボックスを使用すると、パッケージに対する読み取りアクセス権のあるデータベースレベル ロールおよびパッケージに対する書き込みアクセス権のあるデータベースレベル ロールを指定できます。 データベースレベル ロールは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** データベースに格納されたパッケージにのみ適用されます。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] データベースレベルのロールとそのアクセス許可の詳細については、「[Integration Services のロール (SSIS サービス)](security/integration-services-roles-ssis-service.md)」を参照してください。  
  
 ダイアログ ボックスに一覧表示されたロールは、 **msdb** システム データベースの現在のデータベース ロールです。 ロールが選択されていない場合は、既定の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ロールが適用されます。 リーダー ロールには、既定では、 **db_ssisadmin**および **db_ssisoperator**と、パッケージを作成したユーザーが含まれています。 ユーザーがこれらのロールのいずれかのメンバー、またはパッケージを作成したユーザーである場合は、パッケージの列挙、表示、エクスポート、および実行が可能です。 ライター ロールには、既定では、 **db_ssisadmin** と、パッケージを作成したユーザーが含まれています。 ユーザーがこのロールのメンバー、またはパッケージを作成したユーザーである場合は、パッケージのインポート、削除、変更を行うことができます。  
  
 **sysssispackages** テーブルの **ownersid** 列には、パッケージを作成したユーザーの一意なセキュリティ識別子が表示されます。  
  
## <a name="options"></a>および  
 **[パッケージ名]**  
 パッケージの名前を指定します。  
  
 **[リーダー ロール]**  
 ロールを一覧から選択します。  
  
 **[ライター ロール]**  
 ロールを一覧から選択します。  
  
## <a name="see-also"></a>参照  
 [データベース レベルのロール](../relational-databases/security/authentication-access/database-level-roles.md)   
 [セキュリティの概要&#40;Integration Services&#41;](security/security-overview-integration-services.md)  
  
  