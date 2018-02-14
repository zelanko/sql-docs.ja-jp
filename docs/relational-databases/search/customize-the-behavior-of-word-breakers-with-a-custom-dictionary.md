---
title: "ユーザー辞書によるワード ブレーカーの動作のカスタマイズ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: search
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4b984764897fd59b09a5a0eb5b17f76b573fd5b
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
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
  
  
