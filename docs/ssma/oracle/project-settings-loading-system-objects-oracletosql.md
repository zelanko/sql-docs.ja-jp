---
title: "プロジェクトの設定 (読み込みシステム オブジェクト) (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9418cb34-d869-4d24-95b3-6cb9db949bb0
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 0152b483e2617d2b62e5b4f9ba4b88a8f8fa0787
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="project-settingsloading-system-objects-oracletosql"></a>プロジェクトの設定 (読み込みシステム オブジェクト) (OracleToSQL)
[システム オブジェクトの読み込み] ページ、**プロジェクト設定** ダイアログ ボックスでは、SSMA に変換し、読み込みます Oracle システム オブジェクトを指定できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
システム オブジェクトの読み込み ウィンドウで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   すべての SSMA プロジェクトの設定を指定する、**ツール**メニューの **プロジェクト設定の既定の**、設定は表示または変更に必要な移行プロジェクトの種類を選択**移行対象のバージョン**をクリックしてドロップダウン**全般**クリックして、左側のウィンドウの下部にある**システム オブジェクトの読み込み**です。  
  
-   現在のプロジェクトの設定を指定する、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックして、左側のウィンドウの下部にある**システム オブジェクトの読み込み**です。  
  
## <a name="default-settings"></a>既定の設定  
システム オブジェクトを変換するシステム リソースを消費し、時間がかかります。 パフォーマンスを向上させるのには、SSMA は、次の一覧に示すように最もよく使用されるシステム オブジェクトのみを選択します。  
  
-   SYS です。DBMS_OUTPUT  
  
-   SYS です。DBMS_PIPE  
  
-   SYS です。DBMS_UTILITY  
  
-   SYS です。標準  
  
-   SYS です。UTL_FILE  
  
-   SYS です。DBMS_LOB  
  
-   SYS です。DBMS_SQL  
  
-   SYS です。DBMS_SESSION  
  
Oracle オブジェクトは、その他のシステム オブジェクトを参照して、それらのオブジェクトを選択してください。 Oracle データベース オブジェクトによって参照されているシステム オブジェクトを選択しない場合は、SSMA で変換エラーを報告します。 システム オブジェクトの不足によって発生する変換エラーが発生した場合は、このダイアログ ボックスで、不足しているオブジェクトを選択します。 必要に応じて変換を行うことができます。  
  
