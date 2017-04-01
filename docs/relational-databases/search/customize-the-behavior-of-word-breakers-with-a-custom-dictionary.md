---
title: "ユーザー辞書によるワード ブレーカーの動作のカスタマイズ | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# ユーザー辞書によるワード ブレーカーの動作のカスタマイズ
  言語固有のユーザー辞書ファイルを作成することで、特定の言語のワード ブレーカーの動作をカスタマイズできます。 たとえば、特定の用語やパターンがワード ブレーカーによって区切られないようにすることができます。  
  
 詳細については、次の SharePoint の記事を参照してください。  
  
 [ユーザー辞書を作成する (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ユーザー辞書ファイルを次のフォルダーに配置します。  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 ユーザー辞書ファイルの作成または変更後、次のコマンドで SQL フルテキスト デーモン ランチャーを再起動します。  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  