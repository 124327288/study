# https://ffmpeg.zeranoe.com/builds/win32/static/
# https://master.dl.sourceforge.net/project/ffmpegwindowsbi/2016-08-12-v3.1.2/ffmpeg.static.2016-08-12-v3.1.2.32-bit.zip

����ffmpeg����Ƶ���ȡ֡  
ffmpeg -i ��Ƶ·�� -r ÿ���ȡ֡�� ͼƬ����·��  
���ӣ�ffmpeg -i E:/shipin/one.mp4 -r 60 E:/tupian/image%d.jpg  
������ÿ��һ֡���ٶȣ��ӵ� 26 �뿪ʼһֱ��ȡ 7 �볤��ʱ�䣬��ȡ����ÿһ��ͼ�񣬶��� 3 λ�����Զ����ɴ�С������ļ�����  
ffmpeg -i toolba.mkv -r 1 -ss 00:00:26 -t 00:00:07 %03d.png  

�ϳ���Ƶ ���ӣ�
ffmpeg -f image2 -i /home/ttwang/images/image%d.jpg   tt.mp4  
