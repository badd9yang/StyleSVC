# StyleSVC:Singing Voice Conversion with Multi-scale Style Transfer


- [StyleSVC:Singing Voice Conversion with Multi-scale Style Transfer](#stylesvcsinging-voice-conversion-with-multi-scale-style-transfer)
	- [Abstract](#abstract)
	- [Style Transfer Samples](#style-transfer-samples)
	- [Ablation Studies](#ablation-studies)

## Abstract

Singing Voice Conversion (SVC) aims to alter the identity of source singing voice while maintain the content information. However, due to the rich expressiveness of singing voices, current SVC models face limitations in transferring the complex and detailed singing styles (such as timbre, singing methods, pronunciation and singing techniques) of target singers. In this paper, we introduce StyleSVC, a novel model designed to transfer the multi-scale style of a reference singer. First, we propose an RVQ-based style encoder that extracts MIDI note-level fine-grained style features from reference singing voice and seamlessly injects these fine-grained features into content information through cross-attention mechanism. In addition, global style information (including timbre and singing method) is extracted by fine-tuning MERT. Finally, we introduce Uncertain Style Instance Normalization (USIN) to avoid source singer style leakage and balance style and sound quality through an activation strategy with increased probability. Experimental results show that our proposed method surpasses the baseline.

![model](.\assert\pic\model.png)

## Style Transfer Samples

1. **reference global style: ethnic, male**

<table style='width: 50%;'>
	<thead>
		<tr>
            <th style="text-align: center">source(pop, female)</th>
			<th style="text-align: center">Reference(ethnic, male)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_ori.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/0_0_0_reference.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">So-VITS-SVC</th>
			<th style="text-align: center">So-VITS-SVC w predict F0</th>
      		<th style="text-align: center">So-VITS-SVC w GST</th>
            <th style="text-align: center">StyleSVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_so-vits-svc.wav" type="audio/wav"></audio>
            </td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_so-vits-svc_f0.wav" type="audio/wav"></audio></td>
      		<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_so-vits-svc_gst.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_stylesvc.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
    <tbody>
          <tr>
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_so-vits-svc.png" alt="so-vits" style="zoom:19%;" /> </td>  
			<td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_so-vits-svc_f0.png" alt="so-vits_f0" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_so-vits-svc_gst.png" alt="so-vits-gst" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_stylesvc.png" alt="stylesvc" style="zoom:19%;" /></td>  
		</tr>
    </tbody>
</table>

Successfully transferring the timbre, singing techniques.



2. **reference global style: ethnic, female**

<table style='width: 50%;'>
	<thead>
		<tr>
            <th style="text-align: center">source(pop, female)</th>
			<th style="text-align: center">Reference(ethnic, female)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_1_7]_ori.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/0_1_7_reference.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">So-VITS-SVC</th>
			<th style="text-align: center">So-VITS-SVC w predict F0</th>
      		<th style="text-align: center">So-VITS-SVC w GST</th>
            <th style="text-align: center">StyleSVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_1_7]_so-vits-svc.wav" type="audio/wav"></audio>
            </td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_1_7]_so-vits-svc_f0.wav" type="audio/wav"></audio></td>
      		<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_1_7]_so-vits-svc_gst.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_1_7]_stylesvc.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
    <tbody>
          <tr>
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_1_7]_so-vits-svc.png" alt="so-vits" style="zoom:19%;" /> </td>  
			<td><img src="assert\pic\ni_men_22_[1_1_24]to[0_1_7]_so-vits-svc_f0.png" alt="so-vits_f0" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_1_7]_so-vits-svc_gst.png" alt="so-vits-gst" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_1_7]_stylesvc.png" alt="stylesvc" style="zoom:19%;" /></td>  
		</tr>
    </tbody>
</table>


3. **reference global style: pop, male**

<table style='width: 50%;'>
	<thead>
		<tr>
            <th style="text-align: center">source(ethnic, female)</th>
			<th style="text-align: center">Reference(pop, male)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_ori.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/1_0_15_reference.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">So-VITS-SVC</th>
			<th style="text-align: center">So-VITS-SVC w predict F0</th>
      		<th style="text-align: center">So-VITS-SVC w GST</th>
            <th style="text-align: center">StyleSVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_so-vits-svc.wav" type="audio/wav"></audio>
            </td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_so-vits-svc_f0.wav" type="audio/wav"></audio></td>
      		<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_so-vits-svc_gst.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_stylesvc.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
    <tbody>
          <tr>
            <td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_so-vits-svc.png" alt="so-vits" style="zoom:19%;" /> </td>  
			<td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_so-vits-svc_f0.png" alt="so-vits_f0" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_so-vits-svc_gst.png" alt="so-vits-gst" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_0_15]_stylesvc.png" alt="stylesvc" style="zoom:19%;" /></td>  
		</tr>
    </tbody>
</table>

The source singer’s singing skills were removed, and the target singer’s timbre and singing technique were successfully transferred. 



4. **reference global style: pop, female**

<table style='width: 50%;'>
	<thead>
		<tr>
            <th style="text-align: center">source(ethnic, female)</th>
			<th style="text-align: center">Reference(pop, female)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_ori.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/1_1_24_reference.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">So-VITS-SVC</th>
			<th style="text-align: center">So-VITS-SVC w predict F0</th>
      		<th style="text-align: center">So-VITS-SVC w GST</th>
            <th style="text-align: center">StyleSVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_so-vits-svc.wav" type="audio/wav"></audio>
            </td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_so-vits-svc_f0.wav" type="audio/wav"></audio></td>
      		<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_so-vits-svc_gst.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_stylesvc.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
    <tbody>
          <tr>
            <td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_so-vits-svc.png" alt="so-vits" style="zoom:19%;" /> </td>  
			<td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_so-vits-svc_f0.png" alt="so-vits_f0" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_so-vits-svc_gst.png" alt="so-vits-gst" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\jiang_bian_you_ge_xiang_tan_xian_10_[0_1_7]to[1_1_24]_stylesvc.png" alt="stylesvc" style="zoom:19%;" /></td>  
		</tr>
    </tbody>
</table>



## Ablation Studies

We undertake ablation studies to showcase the efficacy of various designs incorporated within StyleSVC.

<table style='width: 50%;'>
	<thead>
		<tr>
            <th style="text-align: center">source(pop, female)</th>
			<th style="text-align: center">Reference(ethnic, male)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_ori.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/0_0_0_reference.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">StyleSVC w/o RSA USIN</th>
			<th style="text-align: center">StyleSVC w/o RSA</th>
      		<th style="text-align: center">StyleSVC w/o USIN</th>
            <th style="text-align: center">StyleSVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_stylesvc_noRSA_USIN.wav" type="audio/wav"></audio>
            </td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_stylesvc_noRSA.wav" type="audio/wav"></audio></td>
      		<td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_stylesvc_noUSIN.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="assert/ni_men_22_[1_1_24]to[0_0_0]_stylesvc.wav" type="audio/wav"></audio></td>
		</tr>
     <tbody>
          <tr>
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_stylesvc_noRSA_USIN.png" alt="so-vits" style="zoom:19%;" /> </td>  
			<td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_stylesvc_noRSA.png" alt="so-vits_f0" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_stylesvc_noUSIN.png" alt="so-vits-gst" style="zoom:19%;" /></td>  
            <td><img src="assert\pic\ni_men_22_[1_1_24]to[0_0_0]_stylesvc_ablation.png" alt="stylesvc" style="zoom:19%;" /></td>  
		</tr>
    </tbody>
</table>


