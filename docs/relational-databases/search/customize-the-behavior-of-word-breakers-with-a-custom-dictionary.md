---
title: ユーザー辞書によるワード ブレーカーの動作のカスタマイズ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7cedd510018ce487d5f6eb61468b1b66ce45ddf9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646290"
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
  
  
