---
title: ユーザー辞書によるワード ブレーカーの動作のカスタマイズ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: search
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7ed98dbddeb1ad4c21c7c95f3437783de38236c1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>ユーザー辞書によるワード ブレーカーの動作のカスタマイズ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  言語固有のユーザー辞書ファイルを作成することで、特定の言語のワード ブレーカーの動作をカスタマイズできます。 たとえば、特定の用語やパターンがワード ブレーカーによって区切られないようにすることができます。  
  
 詳細については、次の SharePoint の記事を参照してください。  
  
 [ユーザー辞書を作成する (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、ユーザー辞書ファイルを次のフォルダーに配置します。  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 ユーザー辞書ファイルの作成または変更後、次のコマンドで SQL フルテキスト デーモン ランチャーを再起動します。  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
