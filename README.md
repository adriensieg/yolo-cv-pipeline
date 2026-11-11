# yolo-cv-pipeline
Yolo Pipeline

### Folder layout: where everything lives

```
yolo_pipeline/
├── config.yaml              # ALL settings (fps, classes, split, hyperparameters)
├── common.py                # shared helpers
├── requirements.txt
├── 01-extract_frames.py ... 07-infer_video.py
├── raw/
│   ├── videos/              # (1) PUT YOUR RAW .mp4 HERE
│   └── footage/             # (auto) frames from step 01
│       └── 2026-11-10/      #   one folder per date (YYYY-MM-DD)
│           └── cam1/        #   one folder per video
│               └── cam1_frame_000001.jpg
├── labelstudio/
│   ├── label_config.xml     # (auto) step 02, paste into Label Studio
│   └── export.json          # (2) PUT THE LABEL STUDIO JSON EXPORT HERE
├── dataset/                 # (auto) step 03, the YOLO dataset
│   ├── images/{train,val,test}/
│   ├── labels/{train,val,test}/   # one .txt per image, empty if no object
│   └── data.yaml
├── runs/                    # (auto) Ultralytics training/eval runs
├── models/                  # (auto) best.pt, last.pt, best.onnx, run_info.json
├── mlflow.db + mlartifacts/ # (auto) MLflow tracking
├── test_videos/             # (3) PUT NEW, UNSEEN .mp4 HERE
└── outputs/                 # (auto) annotated videos + detection CSVs
```

### Step 0: one-time setup
- Use 2 virtual environments

<mark>Pipeline environment (Python 3.10–3.13)</mark>
```
cd yolo_pipeline
python3 -m venv venv-yolo-pipe
pip install -r requirements.txt
```

<mark>Label Studio environment</mark>
```
label-studio
```

Open config.yaml and check classes ([Small, Medium, Large]), extract.fps (3) and the split (70/20/10).


https://github.com/adriensieg/AI-on-Edge/blob/master/Pipeline.md
