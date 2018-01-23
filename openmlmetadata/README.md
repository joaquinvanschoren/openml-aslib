OpenML meta-data
================
Extracts all OpenML evaluation results and dataset meta-features for a specific dataset

Usage
-----
Run by specifying an OpenML study id and evaluation measure:
```
python generate.py --study_id 34 --eval predictive_accuracy
```

See the [complete list of studies](https://www.openml.org/search?q=&type=study). Study 34 and 14 are good starting points.
See the [complete list of evaluation measures](https://www.openml.org/search?q=%2520measure_type%3Aevaluation_measure&type=measure)

Output
------
Appears in the `output` subfolder. Three ARFF files should be generated:

`study_ID_run_evaluations_MEASURE.arff`  
Contains the evaluation results of all OpenML runs in the study. Features:  
* OpenML Task id (can be looked up as www.openml.org/t/TaskID)
* Repetition: counter for runs executed multiple times
* Algorithm: Algorithm name, in format FlowID_FlowName (can be looked up as www.openml.org/f/FlowID)
* Evaluation score (based on MEASURE)
* Run Status: {ok, timeout, memout, not_applicable, crash, other}

`study_ID_metafeatures.arff`  
Contains the computed values for all meta-features known to OpenML. Features:
* OpenML Task id (can be looked up as www.openml.org/t/TaskID)
* Repetition: counter for metafeatures computed multiple times
* [One attribute for each OpenML meta-feature](https://www.openml.org/search?q=%2520measure_type%3Adata_quality&type=measure)

`study_ID_joint_metadata.arff`
Contains the data of both previous tables, joined by Task ID.
