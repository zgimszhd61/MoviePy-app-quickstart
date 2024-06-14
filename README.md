# MoviePy-app-quickstart
以下是一个使用Python库MoviePy的函数，用于将视频剪切成每段10秒钟的短视频：

```python
from moviepy.video.io.ffmpeg_tools import ffmpeg_extract_subclip

def split_video_into_clips(input_video_path, clip_duration=10):
    """
    将视频剪切成每段clip_duration秒的短视频。

    参数:
    input_video_path (str): 输入视频文件的路径。
    clip_duration (int): 每段视频的时长，单位为秒。

    返回:
    None
    """
    from moviepy.editor import VideoFileClip

    # 加载视频文件
    video = VideoFileClip(input_video_path)
    video_duration = int(video.duration)  # 获取视频总时长

    # 计算需要生成的短视频数量
    num_clips = video_duration // clip_duration

    for i in range(num_clips):
        start_time = i * clip_duration
        end_time = start_time + clip_duration
        output_video_path = f"{input_video_path.split('.')[0]}_clip_{i+1}.mp4"
        
        # 使用ffmpeg_extract_subclip函数剪切视频
        ffmpeg_extract_subclip(input_video_path, start_time, end_time, targetname=output_video_path)
        print(f"生成短视频: {output_video_path}")

    # 如果视频总时长不是clip_duration的整数倍，处理剩余部分
    if video_duration % clip_duration != 0:
        start_time = num_clips * clip_duration
        end_time = video_duration
        output_video_path = f"{input_video_path.split('.')[0]}_clip_{num_clips+1}.mp4"
        ffmpeg_extract_subclip(input_video_path, start_time, end_time, targetname=output_video_path)
        print(f"生成短视频: {output_video_path}")

# 示例用法
split_video_into_clips("example_video.mp4", 10)
```

### 解释
1. **导入库**：首先导入`ffmpeg_extract_subclip`函数和`VideoFileClip`类。
2. **加载视频**：使用`VideoFileClip`加载输入视频文件，并获取视频的总时长。
3. **计算短视频数量**：根据视频总时长和每段视频的时长（默认10秒），计算需要生成的短视频数量。
4. **剪切视频**：使用`ffmpeg_extract_subclip`函数将视频剪切成每段10秒的短视频，并保存到指定路径。
5. **处理剩余部分**：如果视频总时长不是10秒的整数倍，处理剩余部分并生成最后一个短视频。

这个函数可以根据需要调整`clip_duration`参数来生成不同时长的短视频。

Citations:
[1] https://www.pythoncentral.io/the-top-3-python-libraries-developers-can-use-for-video-editing/
[2] https://www.youtube.com/watch?v=av1Uuxdo9Z4
[3] https://stackoverflow.com/questions/5619053/whats-a-good-python-library-to-manipulate-frames-of-a-video-file
[4] https://pypi.org/project/moviepy/
[5] https://cloudinary.com/blog/python-video-editing-optimization
[6] https://creatomate.com/how-to/python/trim-a-video
[7] https://fosspost.org/clip-split-large-videos-python
[8] https://shotstack.io/product/sdk/python/
[9] https://github.com/c0decracker/video-splitter
[10] https://towardsdatascience.com/automate-video-editing-with-python-4e0c43edef36
[11] https://www.youtube.com/watch?v=HTKQK-MkBPo
[12] https://www.geeksforgeeks.org/moviepy-getting-cut-out-of-video-file-clip/
[13] https://github.com/Zulko/moviepy
[14] https://stackoverflow.com/questions/65570944/how-to-split-a-video-in-parts-using-python
[15] https://stackoverflow.com/questions/67334379/cut-mp4-in-pieces-python
[16] https://github.com/rezoo/movis
[17] https://www.geeksforgeeks.org/introduction-to-moviepy/
[18] https://shotstack.io/learn/trim-videos-using-python/
[19] https://www.youtube.com/watch?v=SGsJc1K5xj8
[20] https://stackoverflow.com/questions/67334379/cut-mp4-in-pieces-python/67334745
