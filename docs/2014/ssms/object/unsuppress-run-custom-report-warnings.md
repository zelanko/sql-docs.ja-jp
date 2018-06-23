---
title: カスタム レポート実行時の警告の抑制を解除する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d303321941668d5115c3796022f70195b4a0d066
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178584"
---
# <a name="unsuppress-run-custom-report-warnings"></a>カスタム レポート実行時の警告の抑制を解除する方法
  カスタム レポートについて表示される警告ダイアログ ボックスは 2 種類あります。 このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、これらのボックスの表示抑制を解除する方法について説明します。  
  
 既定で、 **[カスタム レポートの実行]** ダイアログ ボックスはカスタム レポートが実行される前に表示されます。 **[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。 また、カスタム レポートを開き、リンクをクリックして別のカスタム レポートを開いたときにも、既定で **[カスタム レポートの実行]** ダイアログ ボックスが表示されます。 このダイアログ ボックスにはドリルスルー カスタム レポート ファイルへの完全パスが表示されます。 **[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>メインのカスタム レポート警告ダイアログ ボックスの抑制を解除するには  
  
1.  接続\<*サーバー*>\\<*共有*>|\<*ドライブ*> \Documents and Settings\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml です。  
  
2.  右クリック`reports.xml`、クリックして**編集**です。  
  
3.  変更**\<SuppressWarning > true\</SuppressWarning > に\<SuppressWarning > false\</SuppressWarning >** です。  
  
4.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を再起動します。  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>ドリルスルー カスタム レポート警告ダイアログ ボックスの抑制を解除するには  
  
1.  接続\<*サーバー*>\\<*共有*>|\<*ドライブ*> \Documents and Settings\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml です。  
  
2.  右クリック`reports.xml`、 をクリック**編集**です。  
  
3.  変更 **\<SuppressDrillthroughWarning > true\</SuppressDrillthroughWarning > に\<SuppressDrillthroughWarning > false\</SuppressDrillthroughWarning >**.  
  
4.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を再起動します。  
  
## <a name="see-also"></a>参照  
 [Management Studio におけるカスタム レポート](custom-reports-in-management-studio.md)   
 [カスタム レポートを Management Studio に追加します。](add-a-custom-report-to-management-studio.md)   
 [カスタム レポートでのオブジェクト エクスプローラー ノード プロパティの使用](use-custom-reports-with-object-explorer-node-properties.md)  
  
  