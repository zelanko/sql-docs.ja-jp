---
title: 既存の項目をプロジェクトに追加する| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81ceb839aa789985bd9de2d43c28c9f01c99af3f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066376"
---
# <a name="add-existing-items-to-a-project"></a>既存の項目をプロジェクトに追加する
  プロジェクトに新しい項目を追加して、アプリケーションの機能を拡張できます。 既存の項目は、クエリやその他のファイルです。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトおよび Analysis Services スクリプト プロジェクトという 2 種類のプロジェクトがあります。 プロジェクトの種類によって、プロジェクトに追加できるクエリ ファイルが決まります。 たとえば、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ (拡張子が .sql のファイル) は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトには追加できますが、Analysis Services スクリプト プロジェクトには追加できません。 追加のファイル拡張子をプロジェクトの種類に関連付ける方法については、「[ファイル拡張子をコードエディターに関連付ける](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)」を参照してください。  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a>既存のクエリまたはその他のファイルをプロジェクトに追加するには  
  
1.  ソリューション エクスプローラーで、対象のプロジェクトを選択します。  
  
2.  **[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。  
  
     **Look in**  
     プロジェクトに追加するファイルまたはフォルダーをこの一覧から指定します。 XML Web サービスや ASP.NET Web アプリケーションの場合、ファイルは Web サーバーに置かれています。  
  
     **[デスクトップ]**  
     デスクトップに存在するファイルおよびフォルダーを表示します。  
  
     **[マイ プロジェクト]**  
     既定の **[マイ プロジェクト]** の場所にあるファイルとフォルダーを表示します。  
  
     **[マイ コンピューター]**  
     **[マイ コンピューター]** フォルダーの内容を表示します。  
  
     **[ファイル名]**  
     このオプションを使用すると、表示するファイルとフォルダーをフィルター選択できます。 フィルター選択するファイル名またはファイル名の一部を入力します。ワイルドカードとしてアスタリスク (`*`) を使用できます。  
  
    > [!NOTE]  
    >  Web およびネットワークの場所に移動するには、 **[ファイル名]** ボックスに URL またはネットワーク パスを入力します。 たとえば、「 **http://mywebsite** 」と入力した場合は、"mywebsite" という Web の場所で利用可能なファイルが表示され、「 **\\\myserver\myshare**」と入力した場合は、"myserver" の "myshare" という場所で利用可能なファイルが表示されます。  
  
     **ファイルの種類**  
     ファイルの拡張子に基づいてファイルをフィルター選択するときに、このオプションを使用します。 各製品について、最も一般的なファイルの種類を対象とする既定のフィルターが一覧表示されます。  
  
     **追加**  
     このドロップダウン ボタンを使用すると、プロジェクトに項目を追加し、その項目を既定のエディターで開くことができます。  
  
    -   **追加**  
  
         既存の項目をディスク上のプロジェクト フォルダーにコピーし、その項目をソリューション エクスプローラーで選択したプロジェクトの下に追加します。 項目に加えられた変更は、元の場所の項目には反映されません。 これは、この種類のファイルの既定のエディターです。  
  
    -   **[リンクとして追加]**  
  
         選択したファイルをプロジェクトに追加し、そのファイルを、ファイルの種類に対応した既定のエディターで開きます。 このオプションでは、最初に選択したファイルが開きます。ファイルがプロジェクト フォルダーにコピーされるわけではありません。  
  
3.  クエリ ファイルを追加する場合は、接続ダイアログが表示され、クエリの接続を指定するように求められます。 クエリに接続を関連付けない場合には、接続ダイアログで **[キャンセル]** をクリックできます。  
  
4.  ファイルがプロジェクトの **[クエリ]** または **[その他]** フォルダーに追加されます。  
  
## <a name="see-also"></a>参照  
 [ソリューション エクスプローラー](solution-explorer.md)   
 [プロジェクトに新しい項目を追加する](add-new-items-to-a-project.md)   
 [アイテムやプロジェクトのクリアまたは削除](remove-or-delete-an-item-or-project.md)  
  
  
