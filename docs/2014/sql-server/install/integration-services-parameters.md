---
title: Integration Services Parameters |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059266"
---
# <a name="integration-services-parameters"></a>Integration Services パラメーター
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、コンピューター上のパッケージを分析するか、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ファイルシステム内のパッケージファイルを分析するかを決定できます。 ファイル システムのファイルを分析する場合は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを含むフォルダーのパスを指定します。  
  
## <a name="options"></a>オプション  
 **[コンピューターの SSIS パッケージを分析する]**  
 コンピューター上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを分析するときは、このオプションを選択します。 既定では、このオプションが選択されています。  
  
 **[SSIS パッケージ ファイルを分析する]**  
 ファイル システムの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを分析するときは、このオプションを選択します。  
  
 **[SSIS パッケージのパス]**  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージが保存されている UNC またはローカル パスを指定します。 ファイル名を含める必要はありません。 入力したパスにアクセスできない場合は、[**次へ**] をクリックすることはできません。 既定では、パスは空白です。 このフィールドは、[ **SSIS パッケージファイルの分析**] を選択した場合にのみ有効になります。  
  
## <a name="see-also"></a>参照  
 [アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
