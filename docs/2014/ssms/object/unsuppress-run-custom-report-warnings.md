---
title: カスタム レポート実行時の警告の抑制を解除する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed653b16fe524f364ba89f13e00715b725080033
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62824397"
---
# <a name="unsuppress-run-custom-report-warnings"></a>カスタム レポート実行時の警告の抑制を解除する方法
  カスタム レポートについて表示される警告ダイアログ ボックスは 2 種類あります。 このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、これらのボックスの表示抑制を解除する方法について説明します。  
  
 既定で、 **[カスタム レポートの実行]** ダイアログ ボックスはカスタム レポートが実行される前に表示されます。 **[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。 また、カスタム レポートを開き、リンクをクリックして別のカスタム レポートを開いたときにも、既定で **[カスタム レポートの実行]** ダイアログ ボックスが表示されます。 このダイアログ ボックスにはドリルスルー カスタム レポート ファイルへの完全パスが表示されます。 **[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>メインのカスタム レポート警告ダイアログ ボックスの抑制を解除するには  
  
1.  \<*サーバー*>|**\\ \>共有> ドライブに接続します。 \documents と Settings<UserProfile \Application Data\Microsoft\Microsoft SQL に接続します。** >\\<\<  
  
2.  を右クリック`reports.xml`し、[**編集**] をクリックします。  
  
3.  **\<SuppressWarning\<>true/SuppressWarning> を SuppressWarning \<>false\</SuppressWarning>に**変更します。  
  
4.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を再起動します。  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>ドリルスルー カスタム レポート警告ダイアログ ボックスの抑制を解除するには  
  
1.  \<*サーバー*>|**\\ \>共有> ドライブに接続します。 \documents と Settings<UserProfile \Application Data\Microsoft\Microsoft SQL に接続します。** >\\<\<  
  
2.  を右クリック`reports.xml`し、[**編集**] をクリックします。  
  
3.  ** \<SuppressDrillthroughWarning\<>true/SuppressDrillthroughWarning>を SuppressDrillthroughWarning \<>false\</SuppressDrillthroughWarning>に**変更します。  
  
4.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を再起動します。  
  
## <a name="see-also"></a>参照  
 [Management Studio のカスタムレポート](custom-reports-in-management-studio.md)   
 [カスタムレポートを Management Studio に追加する](add-a-custom-report-to-management-studio.md)   
 [カスタム レポートでのオブジェクト エクスプローラー ノード プロパティの使用](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
